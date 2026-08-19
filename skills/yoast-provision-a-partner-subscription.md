---
name: yoast-provision-a-partner-subscription
description: >-
  Create, link, renew, cancel or refund a Yoast product subscription on behalf of a
  customer through the MyYoast Provisioning API — the one API Yoast hosts itself, gated
  to approved provisioning partners.
api: MyYoast Provisioning API
generated: '2026-08-13'
method: generated
source: openapi/yoast-myyoast-provisioning-openapi.yml
operations:
  - subscriptionProvisioningControllerCreate
  - subscriptionProvisioningControllerSetSiteForSubscription
  - subscriptionProvisioningControllerGetOne
  - subscriptionProvisioningControllerRenewSubscription
  - subscriptionProvisioningControllerCancelSubscription
  - subscriptionProvisioningControllerRefundSubscription
  - provisioningDownloadsControllerCurrentVersionV2
  - provisioningUsersControllerScheduleDelete
  - provisioningAccountControllerRegenerateToken
---

# Provision a Yoast subscription as a partner

## When to use this

You are a host, agency or reseller with a Yoast provisioning agreement, and you sell
Yoast plugin licences bundled with your own product. This is the only Yoast API that runs
on Yoast infrastructure (`https://my.yoast.com`).

## Before you start

- **You need partner credentials.** Authentication is HTTP Basic with a username and
  password issued by Yoast to provisioners. There is no self-serve signup and no OAuth
  path for this API — despite `my.yoast.com` also running a full OIDC provider for the
  plugin's own site authentication. If you do not have credentials, Yoast's docs say to
  contact them; do not attempt to proceed.
- **These operations move money.** Create, renew, refund and cancel are all billable.
  Read the idempotency warning below before writing any retry logic.

## Steps

1. **Create the subscription** — `subscriptionProvisioningControllerCreate`

   ```
   POST https://my.yoast.com/api/provisioning/subscriptions/create
   ```

   Body (`CreateProvisionedSubscriptionDto`): `customerEmail`, `productCode`, `site`,
   `firstName`, `lastName`. The response (`SubscriptionProvisioningResponseDto`) carries
   `iD`, `subscriptionNumber`, `status`, `startDate`, `endDate`, `pluginDownloadUrls[]`
   and `siteUrl`.

   **Persist `iD` immediately, before doing anything else.** There is no list endpoint —
   `subscriptionProvisioningControllerGetOne` is fetch-by-id only. If you lose the id you
   have no API-side way to find the subscription again.

2. **Link it to the customer's site** — `subscriptionProvisioningControllerSetSiteForSubscription`

   ```
   POST https://my.yoast.com/api/provisioning/subscriptions/{id}/set-site
   ```

   Body (`SetProvisionedSiteDto`): `site`. Note the documented behaviour: *setting* a
   site removes the site if one is already set. It replaces; it does not add. A
   subscription holds one site.

3. **Give the customer their download** — `provisioningDownloadsControllerCurrentVersionV2`

   ```
   GET https://my.yoast.com/api/v2/provisioning/downloads/currentVersion?productCode={code}
   ```

   Returns `versions[]` with `name`, `slug`, `version` and `downloadUrl`. Prefer this v2
   route over `provisioningDownloadsControllerCurrentVersion`, which returns a bare
   version string with no download URL. `provisioningDownloadsControllerCurrentZip`
   302-redirects straight to the zip if you want to stream it.

4. **Renew, cancel or refund as the lifecycle demands.**
   - `POST /api/provisioning/subscriptions/{id}/renew`
   - `POST /api/provisioning/subscriptions/{id}/cancel` — body
     (`CancelProvisionedSubscriptionDto`) takes `immediately: bool`. Omitting it cancels
     at period end; `true` cancels now. Be deliberate: this decides whether the customer
     keeps working plugins for the rest of the paid period.
   - `POST /api/provisioning/subscriptions/{id}/refund`

5. **Handle a GDPR erasure request** — `provisioningUsersControllerScheduleDelete`

   ```
   POST https://my.yoast.com/api/provisioning/user/schedule-delete
   ```

   Yoast's generated client references a `ScheduleDeleteUserDto` but does not ship its
   definition, so the request body shape is **not published**. Confirm it with Yoast
   before wiring this path; do not infer fields.

## Rules and gotchas

- **THERE IS NO IDEMPOTENCY KEY.** This is the most important line in this skill. Yoast
  supports no `Idempotency-Key` header and no client-supplied request id on any
  operation. A `create` that times out may or may not have created a subscription, and a
  blind retry can bill the customer twice. Mitigate on your side: generate your own
  correlation id, record the attempt before you send it, and on any timeout or 5xx
  **reconcile before retrying** rather than retrying by reflex. There is no list endpoint
  to reconcile against, so reconciliation means checking your own record of the returned
  `iD`. Treat renew, cancel and refund the same way.
- **Rotating your password locks out every client instantly.**
  `provisioningAccountControllerRegenerateToken` invalidates the old password the moment
  it is called, and the new one is returned once. Roll it during a maintenance window,
  store the response before you do anything else, and expect 401s from any process still
  holding the old secret.
- **Timestamps are Unix integers here.** `startDate` and `endDate` are integers, while
  every timestamp on Yoast's content APIs is an ISO 8601 string. Two conventions in one
  provider — convert explicitly.
- **No error models are published.** The generated client throws a generic exception and
  declares no error schemas, so beyond 401 and 404 you cannot know the failure shapes in
  advance. Log full response bodies from day one.
- **The edge rate-limits aggressively.** `my.yoast.com` sits behind Cloudflare and
  returns `error code: 1015` as plain text with a 429 — no JSON, no `Retry-After`. Parse
  defensively and back off with jitter.
- **This host is out of scope for Yoast's bug bounty.** The customer portal is excluded,
  though Yoast asks that severe flaws still be reported to security@yoast.com.

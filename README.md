# Donately (donately)

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Donately is an online donation and fundraising platform for nonprofits, churches, and businesses. It provides embeddable donation forms, campaign and peer-to-peer fundraising pages, recurring giving, and donor management. Donately exposes a REST/JSON API at base `https://api.donately.com/v2` (API version 2019-03-15) covering accounts, campaigns, donations, recurring subscriptions, people (donors), fundraisers, forms, and webhooks.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/donately/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/donately/refs/heads/main/apis.yml)

## Access Model

Donately is a hosted SaaS platform (not open source). Anyone with a Donately account can generate an **API token** from the dashboard (Settings → API, at `dash.donately.com/integrations/api`) and call the REST API. Authentication uses **HTTP Basic Auth**: the API token is supplied as the username with an empty password (the token is base64-encoded with a trailing colon). Most endpoints require an `account_id` parameter identifying which account to operate against. The `POST /donations` create endpoint can additionally be called **unauthenticated** for public campaign donations, which is how the embeddable donation form submits gifts from the browser.

There is no separate fee for API access — Donately's cost model is a platform fee on processed donations (4% Standard, 2% Growth at $99/month, or 0% Scale for a $5,000 prepayment up to $1M raised), stacked on top of Stripe/PayPal payment processing fees.

> **Note on grounding:** Donately's API reference (developer.donately.com/api) renders as a JavaScript single-page app that could not be fully crawled. Endpoints and behavior confirmed from documentation and third-party connectors (Tray, Pipedream) are marked **CONFIRMED**; the remaining CRUD endpoints follow Donately's Stripe-style REST conventions and are marked **MODELED** — verify exact paths and verbs against the live reference before relying on them.

## Tags

- Fundraising
- Donations
- Nonprofit
- Payments
- Donor Management
- Recurring Giving

## Timestamps

- **Created:** 2026-07-05
- **Modified:** 2026-07-05

## APIs

### Donately Donations API

Create, list, retrieve, and refund donations against an account or campaign. The create endpoint accepts `donation_type` values of `cc`, `ach`, `cash`, and `paypal` and can be called unauthenticated from public embeddable forms.

- **Human URL:** [https://developer.donately.com/api/](https://developer.donately.com/api/)
- **Base URL:** `https://api.donately.com/v2`

### Donately People API

Manage the people (donors and contacts) attached to an account — create, list, retrieve, and update person records including name, email, and associated giving history.

- **Human URL:** [https://developer.donately.com/api/](https://developer.donately.com/api/)
- **Base URL:** `https://api.donately.com/v2`

### Donately Campaigns API

Create, list, retrieve, update, and delete campaigns — the fundraising pages with goals, titles, and settings that donations and fundraisers are organized under.

- **Human URL:** [https://developer.donately.com/api/](https://developer.donately.com/api/)
- **Base URL:** `https://api.donately.com/v2`

### Donately Fundraisers API

Manage peer-to-peer fundraisers — individual or team fundraising pages created under a campaign, each with its own goal and personal messaging.

- **Human URL:** [https://developer.donately.com/api/](https://developer.donately.com/api/)
- **Base URL:** `https://api.donately.com/v2`

### Donately Subscriptions API

Recurring donation schedules. List subscriptions for an account, retrieve a single subscription by ID, and cancel a subscription. Each subscription generates donations on its configured frequency.

- **Human URL:** [https://developer.donately.com/api/](https://developer.donately.com/api/)
- **Base URL:** `https://api.donately.com/v2`

### Donately Accounts API

Retrieve and manage the accounts (organizations) a token has access to. Most other endpoints require an `account_id` parameter identifying which account to operate against.

- **Human URL:** [https://developer.donately.com/api/](https://developer.donately.com/api/)
- **Base URL:** `https://api.donately.com/v2`

## Common Properties

- [GitHub Organization](https://github.com/donately)
- [LinkedIn](https://www.linkedin.com/company/donately)
- [Website](https://www.donately.com)
- [Documentation](https://developer.donately.com/)
- [Plans](plans/donately-plans-pricing.yml)
- [Rate Limits](rate-limits/donately-rate-limits.yml)
- [Fin Ops](finops/donately-finops.yml)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com

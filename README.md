# Donately (donately)

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

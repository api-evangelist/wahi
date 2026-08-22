# Wahi (wahi)

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

Wahi is a Toronto-headquartered Canadian digital real estate platform and licensed brokerage — Wahi Inc., trading as Wahi Realty Inc., Brokerage — founded in 2021 by Benjy Katchen. It runs a consumer home search, an instant home valuation estimate, market data products (Market Pulse, House Price Index), a Wahi Select REALTOR matching service and a cashback program across Ontario, British Columbia, Alberta, Nova Scotia, Saskatchewan and New Brunswick. Wahi sits in the challenger layer of the Canadian listings value chain and does not own the data it surfaces: Canadian residential listings run through CREA, the single national cooperative that operates REALTOR.ca and the Data Distribution Facility (DDF), and Wahi reaches that data as a member brokerage and through a commercial MLS connectivity vendor (Repliers) rather than by operating a feed of its own. Its real estate API posture is none-published. Probing on 2026-07-26 found no developer portal, no api./developer./developers./docs. subdomain (all fail DNS resolution), no OpenAPI or Swagger document, and no RESO Web API certification, RESO Data Dictionary certification, OData service or `$metadata` document anywhere on its hosts; Wahi does not appear in the RESO certificates directory nor on RESO's Canadian membership roster. The Terms of Use expressly forbid automated access, crawling and scraping, and forbid collecting, copying, storing or redistributing MLS data. The single publicly callable, self-describing API found on any Wahi host is the stock WordPress REST API of its marketing CMS — a content surface, not a real estate developer surface. Wahi is an API consumer, not an API producer.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/wahi/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/wahi/refs/heads/main/apis.yml)

## Tags

- Real Estate
- Canada
- Property Listings
- MLS
- Valuation
- AVM
- PropTech
- Rentals
- Brokerage

## Timestamps

- **Created:** 2026-07-26
- **Modified:** 2026-07-26

## APIs

### Wahi WordPress REST API

The stock WordPress REST API served by Wahi's marketing and Learning Centre CMS at `https://wahi.com/wp-json/`. It is publicly reachable and self-describing: an anonymous GET on the root returns a 319KB JSON discovery document declaring 14 namespaces and 223 routes, and an anonymous GET on `/wp-json/wp/v2/posts` returns published Learning Centre content as JSON. This is CMS infrastructure that Wahi neither documents nor offers as a product — it carries no Wahi developer documentation, no key issuance, no terms of API use and no real estate listing, valuation or transaction capability. It is recorded here because it is the only genuinely public, machine-readable API surface confirmed on a Wahi host.

- **Human URL:** [https://developer.wordpress.org/rest-api/](https://developer.wordpress.org/rest-api/)
- **Base URL:** `https://wahi.com/wp-json`

#### Tags

- WordPress
- Content
- CMS
- REST

#### Properties

- [OpenAPI](openapi/wahi-wp-json-discovery.json) — WordPress REST API discovery document, harvested verbatim 2026-07-26 (HTTP 200)
- [Documentation](https://developer.wordpress.org/rest-api/)

## RESO Posture

**No RESO reference found.** Wahi holds no RESO Web API certification and no RESO Data Dictionary certification at any version. It serves no OData service document, no `$metadata` CSDL document, and makes no reference to the RESO Universal Property Identifier (UPI). It does not appear in the RESO certificates directory ([reso.org/certificates](https://www.reso.org/certificates/), HTTP 200, 416,233 bytes, zero occurrences of "Wahi") nor on RESO's Canadian membership roster ([reso.org/canadian-membership](https://www.reso.org/canadian-membership/), HTTP 200, 19 organizations, Wahi absent). This is the expected Canadian answer: RESO certification is a US industry mandate imposed by NAR on Multiple Listing Services, and Wahi is a data consumer as a licensed member brokerage, not an MLS.

The instructive contrast sits upstream. CREA's REALTOR.ca DDF Web API is documented publicly at [ddfapi-docs.realtor.ca](https://ddfapi-docs.realtor.ca/) (HTTP 200), and its OData metadata document at `https://ddfapi.realtor.ca/odata/v1/$metadata` returns **HTTP 401**. The national contract is real, machine-readable and locked — and Wahi reaches it as a member brokerage and through a commercial vendor, never as something a developer can sign up for.

## Access Gate

**none-published.** There is no developer portal, no API program page, no partner page, no data-licensing page, no application form and no terms of API use. A developer cannot self-serve, cannot apply, and is not offered a partner path. What Wahi does publish is a prohibition: its [Terms of Use](https://wahi.com/ca/en/terms-of-use/) forbid automated means "including spiders, robots, crawlers, data mining tools" and forbid collecting, copying, storing, selling or redistributing MLS data. `robots.txt` additionally disallows `*/graphql` and `/ca/en/real-estate/graphql`, closing the one internal machine route the site has.

**Open data:** none. Canada has no counterpart to HM Land Registry Price Paid or Ordnance Survey open data; provincial land registration is largely privatised, with Teranet operating Ontario's registry under concession.

**Auth model:** no developer auth model is published. `/.well-known/openid-configuration` returns HTTP 403. The consumer site uses first-party session sign-in with Google One Tap. The only documented credential mechanism on any Wahi host is WordPress application passwords, issued through `wp-admin` to CMS users.

**Webhooks, events, SDKs, Postman:** none found. There is no Wahi GitHub organization.

## Common Properties

- [Website](https://wahi.com/ca/en)
- [About](https://wahi.com/ca/en/about-us/)
- [Terms of Service](https://wahi.com/ca/en/terms-of-use/)
- [Privacy Policy](https://wahi.com/ca/en/privacy-policy/)
- [Blog](https://wahi.com/ca/en/learning-centre/)
- [Blog RSS](https://wahi.com/ca/en/feed/)

## Maintainers

- Kin Lane — kin@apievangelist.com

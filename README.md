# Wahi (wahi)

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

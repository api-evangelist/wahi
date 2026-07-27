---
name: Search Canadian property listings on Wahi
description: >-
  Use Wahi's published Listing Search API to find for-sale, for-rent and sold residential
  listings across the Canadian provinces Wahi covers, filtering by geography, price, rooms,
  property type and amenities. Includes the liveness check an agent must run first, because the
  contract is published but the endpoint currently answers 404.
api: openapi/wahi-listing-search-openapi.yaml
spec_url: https://wahi.com/gpt/openapi.yaml
base_url: https://api.prod.wahi.com/gpt
auth: none
operations:
  - searchListings
generated: '2026-07-26'
method: generated
---

# Search Canadian property listings on Wahi

Wahi is a Canadian digital real estate platform and licensed brokerage (Wahi Realty Inc.,
Brokerage). It publishes one OpenAPI: the **Listing Search API**, advertised from
`https://wahi.com/.well-known/ai-plugin.json` and served at `https://wahi.com/gpt/openapi.yaml`.
It has exactly one operation.

## Before you call anything: check liveness

On 2026-07-26 the spec was live (HTTP 200) but the server it declares —
`https://api.prod.wahi.com/gpt` — returned `404 {"message":"Not Found"}` for `/gpt/search` and for
every other path probed. This is a ChatGPT-plugin-era surface left published after its endpoint
went dark, with no Sunset header and no deprecation notice.

So the first step of this skill is a probe, not a query:

1. `GET https://api.prod.wahi.com/gpt/search?first=1`
2. If the response is `404` with body `{"message":"Not Found"}`, **stop**. Do not retry, do not
   guess alternate hosts or paths, and do not fall back to scraping wahi.com — Wahi's Terms of Use
   explicitly forbid automated access, crawling and scraping of the site, and forbid collecting,
   copying, storing or redistributing MLS data. Report to the user that Wahi's published listing
   API is not currently served and point them at `https://wahi.com/ca/en` for the consumer
   experience.
3. If it returns `200` with a `listings` array, continue below.

## Authentication

None. The spec declares no `securitySchemes` and Wahi's plugin manifest declares
`"auth": {"type": "none"}` with `is_user_authenticated: false`. Send no credential — there is no
Wahi developer key programme to obtain one from.

## The operation

`searchListings` — `GET /search`. All 30 parameters are optional query parameters; a bare call
returns active listings sorted by relevance.

**Windowing:** `first` (integer) and `last` (integer). There are no cursors, no total count and no
`Link` header — request a window and read `listings[]`.

**Sorting:** `sortBy` ∈ `relevance | date | distance | listDate | listPrice | price | soldDate |
updatedOn` (default `relevance`); `sortOrder` ∈ `asc | desc` (default `desc`).

**Status:** `active` defaults to `true`. Set `active=false` to get **sold** listings only — this is
how you answer "what sold nearby", and it is a mode switch, not an additive filter.

**Geography:** `coordinatesLatitude` + `coordinatesLongitude` + `distance` (metres), or a free-text
`searchString`.

**Price (CAD):** `minPrice`, `maxPrice`. **Rooms:** `minBeds`/`maxBeds`, `minBaths`/`maxBaths`.

**Property:** `propertyTypes[]` ∈ `Apartment | Detached | SemiDetached | Townhouse | Condominium |
Land | Other`; `listingType` ∈ `Sale | Rent`; `minSquareFt`/`maxSquareFt`;
`minLotWidth`/`maxLotWidth`, `minLotDepth`/`maxLotDepth` (metres); `minParkings`.

**Amenities and flags:** `garage`, `fireplace`, `airConditioning`, `allowPets`, `newlyAdded`,
`highestRatedSchools` (Fraser Institute rating ≥ 7).

Use the enums verbatim — they are case-sensitive as declared in the spec.

## Reading the response

`ListingsResponse` carries one field, `listings[]`. Each `Listing` has `mlsId` (the board's MLS
number — Wahi mints no identifier of its own), `listPrice` / `soldPrice` / `annualTaxAmount` in
CAD, `listDate` / `soldDate` as date-times, `type` (`Sale` | `Rent`), bedroom and bathroom counts
including the Canadian `Plus` variants (`numBedroomsPlus` is basement/den rooms usable as
bedrooms — do not add it to `numBedrooms` silently), `sqft` as a **string** that may be a single
value, a range `X-X`, or a comparative `<X`, `address`, `coordinates`, `geoZoneSeoPath`,
`coverImage` and `url`.

Always surface `url` when presenting a listing to a user, and attribute the data to Wahi and the
originating MLS board.

## Errors

No 4xx or 5xx responses are documented in the spec. Observed envelopes:

- REST: `{"message": "Not Found"}` — a bare message, no code, no type URI, no request id.
- GraphQL (`https://api.prod.wahi.com/graphql`, undocumented and robots-disallowed):
  `{"errors":[{"message":"...","extensions":{"code":"..."}}]}`.

There is no `Idempotency-Key`, no rate-limit header and no request-id header. See
`errors/wahi-problem-types.yml` and `conventions/wahi-conventions.yml`.

## Do not

- Do not call `https://api.prod.wahi.com/graphql`. It is undocumented, introspection is disabled
  (`INTROSPECTION_DISABLED`), and `wahi.com/robots.txt` disallows `*/graphql`.
- Do not scrape `wahi.com` listing pages as a fallback.
- Do not store or redistribute the listing data. Wahi passes CREA/board licence terms through its
  Terms of Use: `https://wahi.com/ca/en/terms-of-use/`.

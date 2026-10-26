# API Style Guides

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

A landscape index and comparative analysis of the public API style guides
that the rest of the industry now copies from. This is a topic repo in
the [API Evangelist Network](https://github.com/api-evangelist) — it
catalogs published style guides rather than profiling a single API
provider, and ships a JSON Schema, JSON-LD context, and controlled
vocabulary so that the individual rules across these very different
documents can be expressed in a single, comparable form.

A "style guide" here means a normative document published by a
company or standards body that tells API designers — internal and
external — how their APIs should look and behave. The audience is API
designers, API platform teams, API governance leads, and the tool
builders (linters, gateways, SDK generators) who need a machine-readable
view of these conventions.

## What is in this repo

- [`apis.yml`](./apis.yml) — APIs.yml index of every style guide
  cataloged here. Each entry has a publisher, canonical URL, license,
  scope (REST / GraphQL / AsyncAPI / etc.), and links to the document's
  Spectral ruleset where one exists.
- [`json-schema/style-guide-rule-schema.json`](./json-schema/style-guide-rule-schema.json)
  — JSON Schema for a single style guide rule. Pulling Zalando rule 100,
  Google AIP-131, and the Microsoft Azure idempotency rule into the same
  shape lets them be filtered, compared, and lifted into Spectral.
- [`json-ld/style-guides-context.jsonld`](./json-ld/style-guides-context.jsonld)
  — JSON-LD context mapping the rule schema to schema.org and a
  `style-guides` vocabulary namespace.
- [`vocabulary/style-guides-vocabulary.yml`](./vocabulary/style-guides-vocabulary.yml)
  — Controlled vocabulary: RFC 2119 keywords, the cross-cutting pillars
  every guide addresses, publisher categorization, and the IETF
  references that guides are increasingly citing normatively.
- [`examples/`](./examples/) — Sample rules expressed in the shared
  schema, drawn from Zalando, Google AIP, Microsoft, PayPal, adidas,
  Cisco, Atlassian, Heroku, GitLab, Kubernetes, and IETF httpapi.

## The landscape

Modern API style guides cluster into four generations:

1. **First-generation enterprise guides** (PayPal, Cisco, Atlassian)
   focused on internal consistency for a single company's product
   portfolio. Published as Markdown in a GitHub repo, occasionally
   archived.
2. **The Zalando inflection point** (Zalando RESTful API Guidelines).
   Open-sourced under CC BY 4.0, structured as numbered MUST/SHOULD/MAY
   rules with cross-references, paired with the Zally linter. Became
   the de-facto template for everyone after it.
3. **Hyperscaler design-review systems** (Google API Improvement
   Proposals, Microsoft REST API Guidelines split into Azure and
   Microsoft Graph). Treat the style guide as a living, individually
   reviewable artifact — Google AIPs are explicitly modeled on Python
   PEPs.
4. **The IETF cross-vendor layer** (RFC 9457 Problem Details, RFC 9745
   Deprecation, RFC 9727 api-catalog, the expired but widely-implemented
   Idempotency-Key and RateLimit-headers drafts). Style guides at every
   tier now cite these RFCs rather than inventing their own headers and
   error envelopes.

## Cataloged guides

| Guide | Publisher | Scope | License | Style |
| --- | --- | --- | --- | --- |
| [Microsoft REST API Guidelines](https://github.com/microsoft/api-guidelines) | Microsoft | REST (+ Azure, Graph) | CC BY 4.0 | Companion Azure and Graph documents under one umbrella |
| [Google API Improvement Proposals](https://google.aip.dev/) | Google | REST, gRPC | CC BY 4.0 / Apache-2.0 | 70+ numbered AIPs, PEP-style |
| [Zalando RESTful API and Event Guidelines](https://opensource.zalando.com/restful-api-guidelines/) | Zalando | REST, Events | CC BY 4.0 | 150+ numbered MUST/SHOULD/MAY rules |
| [PayPal API Standards](https://github.com/paypal/api-standards) | PayPal | REST | (archived; mirrored at KuSh/api-standards) | Service Design + Patterns + Hypermedia |
| [adidas API Guidelines](https://github.com/adidas/api-guidelines) | adidas | REST, AsyncAPI | MIT | Prose + bundled Spectral ruleset |
| [Cisco REST API Design Guide](https://github.com/CiscoDevNet/api-design-guide) | Cisco | REST | Cisco copyright | Cross-business-unit narrative |
| [Atlassian REST API Design Guidelines](https://developer.atlassian.com/server/framework/atlassian-sdk/atlassian-rest-api-design-guidelines-version-1/) | Atlassian | REST | Atlassian terms | Server framework v1 |
| [Heroku Platform API Design Conventions](https://devcenter.heroku.com/articles/platform-api-reference) | Heroku | REST | Heroku terms | Embedded in API reference + compatibility policy |
| [GitLab API Style Guide](https://docs.gitlab.com/ee/development/api_styleguide.html) | GitLab | REST, GraphQL | CC BY-SA 4.0 | Developer-contributor focused |
| [Kubernetes API Conventions](https://github.com/kubernetes/community/blob/master/contributors/devel/sig-architecture/api-conventions.md) | Kubernetes / CNCF | REST, Kubernetes | Apache-2.0 (repo) | SIG Architecture canonical doc |
| [IETF httpapi WG Drafts / RFCs](https://datatracker.ietf.org/wg/httpapi/documents/) | IETF | HTTP, REST | IETF Trust | Cross-vendor RFC-track |

## Comparing the pillars

Every guide chooses different defaults for the same handful of decisions.
This matrix is what makes the topic interesting: when you sit down to
write your own style guide, the question is rarely "is there a
convention?" — it is "which of these conventions am I adopting and what
am I trading off?"

| Pillar | Zalando | Google AIP | MS Azure | PayPal | Heroku | IETF reference |
| --- | --- | --- | --- | --- | --- | --- |
| **Versioning** | Media type (vendor) + careful compatibility rules | api-version (date) — see [AIP-185](https://google.aip.dev/185) | `api-version=YYYY-MM-DD` query | Path: `/v{major}/...` | Versioned media type: `application/vnd.heroku+json; version=3` | — |
| **Errors** | Problem JSON | Standard error model with `code`/`message`/`status` (AIP-193) | `ErrorDetail` with code/message/target/innererror; `x-ms-error-code` header | Custom `{ name, message, debug_id, details, links }` | `{ id, message, url }` | **RFC 9457 application/problem+json** |
| **Pagination** | Cursor — `next` link in response | `page_size` + opaque `page_token` (AIP-158) | `nextLink` (absolute URL) + value array | Multiple acceptable strategies | `Range` header + `Next-Range` (206) | — |
| **Naming** | snake_case JSON; kebab-case paths; US English (rule 103) | snake_case proto field names mapped to camelCase JSON (AIP-140) | camelCase JSON | snake_case JSON; lowercase kebab path | snake_case JSON | — |
| **Idempotency** | Required for retry-safe methods | Standard methods are idempotent by design | All operations including POST must be idempotent | `PayPal-Request-Id` header on POSTs | Standard HTTP semantics | **Idempotency-Key draft** (expired but widely implemented) |
| **Headers** | Lots of normative coverage | Sparse | Mandates `x-ms-error-code`, `Repeatability-*` | Sparse | `RateLimit-Remaining`, custom `Range`/`Next-Range` | Link-Template (RFC 9652), Deprecation (RFC 9745), api-catalog (RFC 9727) |
| **Deprecation** | Rules + Deprecation header | Sunset notice + AIP-180 backwards compat | Versioned out via api-version + extensible enums | Documented deprecation policy | API Compatibility Policy article | **RFC 9745 Deprecation header** |
| **Hypermedia** | Optional (rule guidance) | Not emphasized | Optional | Required (HATEOAS Link Description Objects) | Schema discovery via `/schema` endpoint | — |
| **Stability** | Compatibility rules | Stability levels (AIP-181) | Preview vs. stable api-version suffix | Lifecycle states | Per-resource `prototype` / `development` / `production` annotation | — |

(See the [vocabulary](./vocabulary/style-guides-vocabulary.yml) for the
full pillar list and which guides cover each one.)

## Why this repo exists

In the API Evangelist network this topic sits next to three companions:

- [`rules/`](https://github.com/api-evangelist/rules) — Spectral rule
  bundles that *operationalize* style guide rules into linters that gate
  CI.
- [`policies/`](https://github.com/api-evangelist/policies) — the
  policy layer that wraps multiple rules into governable, organizational
  commitments.
- [`design-standards/`](https://github.com/api-evangelist/design-standards)
  — the parent topic that situates API style guides among accessibility
  standards, design systems, and product design guidelines.

This repo is the "design intent" layer — the documents that say *what*
APIs should look like. The rules repo is the "enforcement" layer — the
Spectral rulesets that mechanize the intent. The policies repo is the
"commitment" layer — the organizational stance that says we will run
those rulesets in CI.

## Schema and vocabulary

The rule schema deliberately accepts rules from heterogeneous guides:

- `id` — `zalando-100`, `aip-131`, `ms-azure-versioning`, `rfc-9457`
- `guide` — one of the catalogued style guides
- `level` — RFC 2119 keyword
- `category` — one of the cross-cutting pillars
- `appliesTo` — REST, GraphQL, AsyncAPI, gRPC, OData, Kubernetes, HTTP
- `spectralRule` — optional mapping to a Spectral lint rule that
  enforces the same intent against an OpenAPI document
- `relatedRules` — cross-references to equivalent rules in other guides
  (so an AIP-193 errors rule can point at PayPal errors and RFC 9457)

The vocabulary file groups guides by publisher category (hyperscaler,
commerce/retail, networking, PaaS, standards body), lists every IETF
reference now cited normatively by major guides, and enumerates the
pillars.

## Contributing a new style guide

To add a guide to this index:

1. Add an entry to `apis.yml` with `aid: style-guides:{slug}`,
   `humanURL`, `tags`, and a `Scope` properties block describing
   surfaces, publisher, license, and status.
2. Add at least one representative rule to `examples/` using the JSON
   Schema in `json-schema/`. Use `id` of the form `{slug}-{rule}` and
   set `guide` to the new aid.
3. If the guide ships its own Spectral ruleset, link it as a
   `SpectralRuleset` property in `apis.yml`.
4. Update the pillar matrix in this README if the guide takes a
   distinctive position on any pillar.

## License

Content in this repo is published under the same terms as the rest of
the API Evangelist network. Each linked guide retains its own license
(see the table above). Verbatim quotes from guides are limited to brief
anchoring statements under fair use.

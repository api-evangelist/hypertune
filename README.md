# Hypertune (hypertune)

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
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Hypertune is a type-safe, Git-based platform for feature flags, A/B testing, experimentation, analytics, and app configuration. Flag logic is authored in Hyperlang and modeled as a GraphQL schema; SDKs use a CLI to generate fully typed clients, fetch flag logic once from Hypertune Edge (Cloudflare CDN) at initialization, then evaluate flags locally and synchronously in memory. A GraphQL Edge API offers a no-SDK path, and analytics events are flushed back to Hypertune Edge in the background.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/hypertune/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/hypertune/refs/heads/main/apis.yml)

## Tags

- Feature Flags
- Experimentation
- A/B Testing
- Analytics
- App Configuration
- GraphQL
- Edge

## Timestamps

- **Created:** 2026-06-20
- **Modified:** 2026-06-20

## APIs

### Hypertune Flag Evaluation / Config (GraphQL / SDK) API

Evaluate feature flags, experiments, and app configuration. Flag logic is defined in Hyperlang and exposed as a GraphQL schema; queries to Hypertune Edge must supply all field arguments (the targeting context) so logic is fully reduced to a JSON result. Typically used through the type-safe TypeScript SDK and CLI-generated client, with a token-authenticated GraphQL Edge endpoint available for no-SDK access.

- **Human URL:** [https://docs.hypertune.com/concepts/graphql-api](https://docs.hypertune.com/concepts/graphql-api)
- **Base URL:** `https://edge.hypertune.com/graphql`

#### Tags

- Feature Flags
- GraphQL
- SDK
- Configuration

#### Properties

- [Documentation](https://docs.hypertune.com/concepts/graphql-api)
- [API Reference](https://docs.hypertune.com/getting-started/graphql-quickstart)
- [OpenAPI](openapi/hypertune-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [GraphQL](graphql/hypertune-graphql.md) — [GraphQL Specification](https://spec.graphql.org/)
- [Postman Collection](collections/hypertune.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/hypertune.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Hypertune Edge Config Delivery API

Edge-delivered flag logic. SDKs make a single network request at initialization to fetch the project's flag logic from Hypertune Edge, served from Cloudflare CDN so there is no direct dependency on application servers, then evaluate flags locally and synchronously in memory and listen for logic updates in the background.

- **Human URL:** [https://docs.hypertune.com/concepts/architecture](https://docs.hypertune.com/concepts/architecture)
- **Base URL:** `https://edge.hypertune.com`

#### Tags

- Edge
- CDN
- Configuration
- Initialization

#### Properties

- [Documentation](https://docs.hypertune.com/concepts/architecture)
- [API Reference](https://docs.hypertune.com/sdk-reference/initialization)
- [OpenAPI](openapi/hypertune-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/hypertune.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/hypertune.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Hypertune Analytics / Events API

Real-time analytics and event logging. SDKs collect flag evaluations, experiment exposures, and analytics events (logged via event-trigger flags that evaluate a "Log event" expression) and flush them to Hypertune Edge in the background; flushLogs can be awaited in serverless environments to guarantee delivery.

- **Human URL:** [https://docs.hypertune.com/analytics/guide](https://docs.hypertune.com/analytics/guide)
- **Base URL:** `https://edge.hypertune.com`

#### Tags

- Analytics
- Events
- Experimentation
- Logging

#### Properties

- [Documentation](https://docs.hypertune.com/analytics/guide)
- [API Reference](https://docs.hypertune.com/analytics/overview)
- [OpenAPI](openapi/hypertune-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/hypertune.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/hypertune.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Hypertune Management API

Programmatic and Git-based management of flags, experiments, and configuration. Hypertune versions all flags, experiments, analytics events, and app configuration together in a single Git-based history; bidirectional Git repo sync, API access, and bulk user management are offered on the Enterprise plan.

- **Human URL:** [https://docs.hypertune.com/pricing/overview](https://docs.hypertune.com/pricing/overview)
- **Base URL:** `https://edge.hypertune.com`

#### Tags

- Management
- Git Sync
- Administration
- Enterprise

#### Properties

- [Documentation](https://docs.hypertune.com/pricing/overview)
- [API Reference](https://docs.hypertune.com/getting-started/set-up-hypertune)

## Common Properties

- [GitHub Organization](https://github.com/hypertunehq)
- [LinkedIn](https://www.linkedin.com/company/hypertune)
- [Website](https://www.hypertune.com)
- [Documentation](https://docs.hypertune.com)
- [Plans](plans/hypertune-plans-pricing.yml)
- [Rate Limits](rate-limits/hypertune-rate-limits.yml)
- [Fin Ops](finops/hypertune-finops.yml)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com

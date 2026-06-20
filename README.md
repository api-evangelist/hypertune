# Hypertune (hypertune)

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

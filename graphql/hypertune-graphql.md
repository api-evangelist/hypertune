# Hypertune GraphQL Schema

Conceptual, representative GraphQL schema for the [Hypertune](https://www.hypertune.com/)
feature-flag, experimentation, analytics, and app-configuration platform.

GraphQL is the native model for Hypertune: flag logic authored in **Hyperlang** is
projected as a per-project GraphQL schema, and the type-safe SDK uses a CLI to
generate a fully typed client from that schema. The same logic can be queried
directly over the **GraphQL Edge API** with no SDK.

- GraphQL API docs: <https://docs.hypertune.com/concepts/graphql-api>
- GraphQL quickstart: <https://docs.hypertune.com/getting-started/graphql-quickstart>
- Architecture: <https://docs.hypertune.com/concepts/architecture>
- GitHub: <https://github.com/hypertunehq>

> **Representative schema.** Hypertune generates a unique GraphQL schema per project
> from your flag tree, so the exact types, field names, and arguments differ for every
> account. The schema below in [`hypertune-schema.graphql`](./hypertune-schema.graphql)
> is a representative, illustrative model of the `root(context: ...)` query surface and
> the common flag/experiment/event shapes — it is not the schema of any specific project.

---

## Overview

The Hypertune GraphQL surface is rooted at a single `root` query field that takes a
`context` argument (environment plus targeting attributes such as user identity). Because
flag logic must be **fully reduced** to a JSON result on the edge, every field argument
required by your flag logic must be supplied in the query — Hypertune evaluates the logic
against the provided context and returns concrete values.

- **Endpoint:** `GET https://edge.hypertune.com/graphql`
- **Auth:** URL-encoded project `token` query parameter (`?token=${YOUR_URL_ENCODED_TOKEN}`)
- **Query transport:** the GraphQL query and variables are passed URL-encoded on the GET
  request alongside the token; responses are served from Hypertune Edge (Cloudflare CDN),
  typically in under 25ms.
- **SDK path:** the TypeScript SDK fetches this logic once at initialization and then
  evaluates flags locally, synchronously, in memory.

---

## Schema file

See [`hypertune-schema.graphql`](./hypertune-schema.graphql) for the full representative schema.

---

## Type inventory

### Scalars
| Scalar | Purpose |
|--------|---------|
| `JSON` | Arbitrary JSON payloads (event properties, config blobs) |
| `DateTime` | ISO-8601 timestamps |

### Enums
| Enum | Values |
|------|--------|
| `Environment` | DEVELOPMENT, PREVIEW, PRODUCTION |

### Input types
- `Context` — wraps environment plus the targeting `user` and arbitrary attributes
- `UserInput` — common targeting attributes (id, name, email)

### Object types
- `Query` — root with the `root(context: Context!)` entry point
- `Root` — the reduced flag tree for a given context; exposes flags, experiments, config
- `Experiment` — variant assignment and exposure metadata for an A/B test
- `EventLog` — result envelope for an event-trigger ("Log event") evaluation
- `Mutation` — represents the background log flush (`logEvent`)

---

## Query examples

### Evaluate a boolean flag for a user
```graphql
query TestQuery {
  root(
    context: {
      environment: "development"
      user: { id: "test_id", name: "Test", email: "test@test.com" }
    }
  ) {
    exampleFlag
  }
}
```

### Resolve an experiment variant and config value
```graphql
query {
  root(
    context: {
      environment: "production"
      user: { id: "user_123", email: "user@example.com" }
    }
  ) {
    checkoutExperiment {
      variant
      payload
    }
    maxUploadSizeMb
  }
}
```

### Log an analytics event (background flush)
```graphql
mutation {
  logEvent(
    context: { environment: "production", user: { id: "user_123" } }
    name: "signup_completed"
    properties: { plan: "pro" }
  ) {
    accepted
  }
}
```

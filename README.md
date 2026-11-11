# Serverless Functions

The common serverless vocabulary -- functions, their deployments or versions, and their invocations -- distilled from the edge and function-platform APIs that already exist. Part of [Schema Commons](https://github.com/api-commons/schema-commons),
published by the [API Commons](https://apicommons.org).

Built from the providers tagged Serverless, Functions as a Service, Edge Computing, Edge Functions, Cloud Functions, Workers in [APIs.io](https://apis.io) that
publish their own OpenAPI. Only harvested contracts count -- nothing API Evangelist
generated. Every number below is a count of providers.

## What the market already agrees on

<!-- commons:summary -->
| Concept | Expose it | Readable schema | Core properties (share) | Collection named |
| --- | ---: | ---: | --- | --- |
| function | 22 | 20 | name 85%, id 75%, status 50% | functions 17, function 5, workers 3, scripts 1 |
| function_deployment | 7 | 6 | created_at 67%, id 50%, name 50%, status 50%, updated_at 50%, version 50% | deployments 5, versions 3, deployment 1 |

Cohort: 136 providers with harvested OpenAPI, 22 crosswalks. Of the providers exposing a function: 64% create, 96% list, 96% fetch, 59% update, 77% delete. Generated 2026-11-11 by build.py.
<!-- /commons:summary -->

Shares are of the providers with a readable resource schema for that concept. The
extended tier and the long tail of every concept are in [profile.yml](profile.yml).

## What the measurement shows

- Functions agree on name, id and status; runtime, memory and timeout each fall below 30%, because edge platforms fix the runtime and size that cloud function platforms make configurable.
- Function deployments (versions, builds) agree on created_at, id, name, status, updated_at and version at the 6 readable providers that expose them.

## Artifacts

- [openapi.yml](openapi.yml) -- OpenAPI 3.1 of the shared operations. No one serves it; it
  is the shape to map to. Lints clean against the
  [naming ruleset](https://github.com/api-commons/schema-commons/blob/main/ruleset/schema-commons-naming.yaml).
- [schema/](schema) -- JSON Schema 2020-12 per concept; each property carries
  `x-commons-tier`, `x-commons-share`, `x-commons-providers` and the spellings seen.
- [crosswalk/](crosswalk) -- one per provider, common name -> their name, with the harvested
  spec and operations each mapping was read from.
- [adopters.yml](adopters.yml) -- who exposes which concept, linked to their APIs.io page.
- [concepts.yml](concepts.yml) -- the only hand-written input: concepts, path segments and
  their qualifiers, aliases, reviewed exclusions, merged duplicates, and the decisions below.
- [census/](census) -- the cohort and the raw census the profile is built from.

## Decisions

These are calls, not measurements, recorded so they can be revisited as the method matures.

- Workers, scripts, edge functions and lambdas are all function. Invocations were dropped: an invocation is the function's own HTTP call, not a platform resource.

## Rebuild

```bash
../schema-commons/scripts/run.sh .
```

## License

Artifacts CC BY-NC-SA 4.0 ([LICENSE](LICENSE)); code Apache 2.0 ([LICENSE-CODE](LICENSE-CODE)).

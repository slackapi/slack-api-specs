# Web API specifications changelog

#### April 2020

We fixed up the scripts that generate OpenAPI specs for us and have updated the spec to include many new methods and more solid schemas across the board. Full Block Kit schemas are still unavailable.

The biggest recent change to note is that all IDs generated on Slack may now be longer than previously declared in the spec.

Note: it's possible to use `slack_web_openapi_v2.json` to generate a Postman Collection, but you must first modify the spec to be technically and factually invalid unfortunately. Add a top-level `"openapi": "3.0"` attribute near where `"swagger": "2.0"` is defined. `openapi` isn't a valid attribute for OpenAPI 2.0 schemas, and if it were, the version _should_ be `2.0`. Quirky. Postman also doesn't pick up the defined hostname and path `https://slack.com/api` that precedes all Web API method (for example, `https://slack.com/api/chat.postMessage`).

We also now include a version of the spec without inline response examples, but still including response schemas. This might help you get the spec to work with particularly onerous validators.

#### July 2019

We finally made some updates after a long dormant period. Thanks for bearing with us.

Our specifications are programmatically generated from a collection of internal metadata and JSON Schema. As schemas improve or made more correct, the OpenAPI spec evolves. We try to incorporate reported issues in each release.

* Brought OpenAPI 2.0 specification up to date with most of our internal metadata and JSON schema systems.
    - Because OpenAPI 2.0 uses a _subset_ (and sometimes a _superset_) of JSON Schema, some schema definitions are modified in translation and not as expressive as reality. In particular, expressing the `oneOf` instruction is difficult and we replace this nuance with the generic `items`.
    - Many of our schemas are improved and no longer require copious use of `additionalProperties` to be described.
* Removed [`rtm.start`](https://api.slack.com/methods/rtm.start) from the method catalog. Its response varies and we strongly recommend developers to use [`rtm.connect`](https://api.slack.com/methods/rtm.start) instead.
* Removed some of the `search.*` methods from the catalog due to varied responses that cannot yet pass validation. We'll add these back in the next release.
* Added a bare bones `definitions/blocks` schema. We'd like to provide finer grained schema for [Block Kit](https://api.slack.com/block-kit) in the future.
* 132 methods now have well-defined response schema.
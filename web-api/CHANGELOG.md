# Web API specifications changelog

#### August 2020

A number of new methods, especially for admins, have been added to the API recently and are now accounted for here.

Deprecated methods that precede the Conversations API are no longer listed in the specification. [Learn more](https://api.slack.com/changelog/2020-01-deprecating-antecedents-to-the-conversations-api).

As usual, many clarifications as we harden our internal schema. 

We're really looking forward to generating an OpenAPI 3.0 spec for you soon, as well as release more schema for Block Kit.

Thanks for hanging in there.

#### April 2020

We fixed up the scripts that generate OpenAPI specs for us and have updated the spec to include many new methods and more solid schemas across the board. Full Block Kit schemas are still unavailable.

The biggest recent change to note is that all IDs generated on Slack may now be longer than previously declared in the spec.

We now include a version of the spec without inline response examples, but still including response schemas. This might help you get the spec to work with particularly onerous validators.

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
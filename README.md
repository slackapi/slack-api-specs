# slack-api-specs

This repository contains API specifications of Slack platform features and APIs.

## ⚠️ Not Accepting Contributions

Because our specifications are _artifacts_ of an incredible machine, we cannot accept pull requests for this repo. Please file issues with suggestions or bugs with the spec itself. Feedback about the APIs or features the specs describe should be directed to Slack's [developer support team](mailto:feedback@slack.com).

## Overview

You'll find [OpenAPI specs](https://swagger.io/specification/) for the [Slack Web API](https://api.slack.com/web) and [AsyncAPI](https://www.asyncapi.com/v1/guide/) specs for the [Events API](https://api.slack.com/events-api).

Read more about our open specification strategy in [this announcement](https://medium.com/slack-developer-blog/standard-practice-slack-web-openapi-spec-daaad18c7f8).

### Specification menu

* [Web API](web-api)
    - [OpenAPI 2.0 spec](web-api/slack_web_openapi_v2.json) - covers user and bot user token usage of public [Web API](https://api.slack.com/web) methods
* [Events API](events-api)
    - [AsyncAPI 1.0 spec](events-api/slack_events_api_async_v1.json) - a catalog of JSON schema for basic [Events API](https://api.slack.com/events-api) structure and a handful of detailed event types
    - [JSON Schema](events-api/slack_common_event_wrapper_schema.json) - covers only the basic event wrapper all event types delivered by Slack

We continue to refine and expand schema and example coverage throughout all of our specifications.

### How the specs are made

We use a combination of internal metadata, custom scripting, and old fashioned writing-by-hand to produce these specifications. They don't always tell the whole truth and are subject to author and operator error. They are really useful though.


## Recent changes

Now we'll recount the major changes found in each new release of our specifications.

* [Web API specifications changelog](web-api/CHANGELOG.md)


## Using with external tools

### Postman

It's possible to use `slack_web_openapi_v2.json` to generate a Postman Collection, but you must first modify the spec to be technically and factually invalid unfortunately.

Add a top-level `"openapi": "3.0"` attribute near where `"swagger": "2.0"` is defined. While `openapi` isn't a valid attribute for OpenAPI 2.0 schemas, and if it were, the version _should_ be `2.0`. Being wrong this way instructs Postman to do continue importing as a collection.

Postman doesn't pick up the defined hostname and path `https://slack.com/api` that precedes all Web API methods (for example, `https://slack.com/api/chat.postMessage`) as the `{{baseUrl}}` variable for the collection.

Populate {{baseUrl}} by first hovering over your collection in the navigation bar click on the action menu that appears. Then, select "Edit". A modal will appear. Click into the rightmost section, _Variables_ which should have a green dot next to it. In the _Initial Value_ column next to `baseUrl`, enter `https://slack.com/api` and then click _Reset All_. Once you see that both the initial and current values have been set, click update and your imported collection will properly use "https://slack.com/api" as its base domain.

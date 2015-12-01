## Introduction

The Designer News API v2 provides a simple HTTP-based, REST-based mechanism for interacting with Designer News. It uses [OAuth 2.0](http://oauth.net/2/) as an authentication mechanism, and the [JSON API](http://jsonapi.org/) for all request and response payloads.

Our discovery of JSON API fixes a lot of problems with the first version of the Designer News API, namely: consistency and performance. JSON API is predictable and consistent in how it is structured, allowing libraries to increase the amount of code reuse.

Because JSON API has a very sensible way of relating to linked documents, e.g. which stories has a user posted, this allows us to cut down on the nesting of data in responses. With less nesting, the response paylods become smaller. This can have a big effect on mobile clients, where bandwidth could be limited.

If you would like to include the linked resources in a response, [that’s easy too](http://jsonapi.org/format/#fetching-includes).

### About this document

If you find any mistakes or need clarification in a certain section, please open an issue or a pull
request.

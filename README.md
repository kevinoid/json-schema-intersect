JSON Schema Intersect
=====================

[![Build Status](https://img.shields.io/github/actions/workflow/status/kevinoid/json-schema-intersect/node.js.yml?branch=main&style=flat&label=build)](https://github.com/kevinoid/json-schema-intersect/actions?query=branch%3Amain)
[![Coverage](https://img.shields.io/codecov/c/github/kevinoid/json-schema-intersect/main.svg?style=flat)](https://app.codecov.io/gh/kevinoid/json-schema-intersect/branch/main)
[![Dependency Status](https://img.shields.io/librariesio/release/npm/json-schema-intersect.svg?style=flat)](https://libraries.io/npm/json-schema-intersect)
[![Supported Node Version](https://img.shields.io/node/v/json-schema-intersect.svg?style=flat)](https://www.npmjs.com/package/json-schema-intersect)
[![Version on NPM](https://img.shields.io/npm/v/json-schema-intersect.svg?style=flat)](https://www.npmjs.com/package/json-schema-intersect)

A library to combine multiple [JSON Schemas](https://json-schema.org) into a
single schema which matches instances which are valid for all of the combined
schemas.  This is useful for supporting older JSON Schema versions which lack
support for
[`allOf`](https://json-schema.org/draft/2020-12/json-schema-core#name-allof),
such as [JSON Schema Draft
4](https://tools.ietf.org/html/draft-zyp-json-schema-04#section-3.5) used by
[Swagger/OpenAPI 2](https://spec.openapis.org/oas/v2.0.html#schema-object).
The combined schema behaves as closely as possible to a schema with
[`allOf`](https://json-schema.org/draft/2020-12/json-schema-core#name-allof).
containing each of the input schemas.

[!IMPORTANT]
Use [`allOf`](https://json-schema.org/draft/2020-12/json-schema-core#name-allof)
to create a combined schema when possible.


## Introductory Example

```js
import assert from 'node:assert/strict';
import jsonSchemaIntersect from 'json-schema-intersect';

assert.deepEqual(
  jsonSchemaIntersect(
    {
      type: 'number',
      minimum: 5,
      maximum: 15,
    },
    {
      type: 'number',
      minimum: 0,
      maximum: 10,
    },
  ),
  {
    type: 'number',
    minimum: 5,
    maximum: 10,
  },
);
```


## Features

- Supports Schema objects from
  [Swagger/OpenAPI 2](https://spec.openapis.org/oas/v2.0.html#schema-object)
  and [OpenAPI 3](https://spec.openapis.org/oas/v3.0.0.html), including
  `nullable`, `readOnly`, `writeOnly`, and other constraints.


## Installation

[This package](https://www.npmjs.com/package/json-schema-intersect) can be
installed using [npm](https://www.npmjs.com/), either globally or locally, by
running:

```sh
npm install json-schema-intersect
```


## Recipes

More examples can be found in the [test
specifications](https://kevinoid.github.io/json-schema-intersect/spec).


## API Docs

To use this module as a library, see the [API
Documentation](https://kevinoid.github.io/json-schema-intersect/api).


## Contributing

Contributions are appreciated.  Contributors agree to abide by the [Contributor
Covenant Code of
Conduct](https://www.contributor-covenant.org/version/1/4/code-of-conduct.html).
If this is your first time contributing to a Free and Open Source Software
project, consider reading [How to Contribute to Open
Source](https://opensource.guide/how-to-contribute/)
in the Open Source Guides.

If the desired change is large, complex, backwards-incompatible, can have
significantly differing implementations, or may not be in scope for this
project, opening an issue before writing the code can avoid frustration and
save a lot of time and effort.


## License

This project is available under the terms of the [MIT License](LICENSE.txt).
See the [summary at TLDRLegal](https://tldrlegal.com/license/mit-license).

# @hishprorg/porro-animi-eius <sup>[![Version Badge][npm-version-svg]][package-url]</sup>

[![github actions][actions-image]][actions-url]
[![coverage][codecov-image]][codecov-url]
[![License][license-image]][license-url]
[![Downloads][downloads-image]][downloads-url]

[![npm badge][npm-badge-png]][package-url]

Is this value a JS SharedArrayBuffer? This module works cross-realm/iframe, does not depend on `instanceof` or mutable properties, and despite ES6 Symbol.toStringTag.

## Example

```js
var assert = require('assert');
var isSharedArrayBuffer = require('@hishprorg/porro-animi-eius');

assert(!isSharedArrayBuffer(function () {}));
assert(!isSharedArrayBuffer(null));
assert(!isSharedArrayBuffer(function* () { yield 42; return Infinity; });
assert(!isSharedArrayBuffer(Symbol('foo')));
assert(!isSharedArrayBuffer(1n));
assert(!isSharedArrayBuffer(Object(1n)));

assert(!isSharedArrayBuffer(new Set()));
assert(!isSharedArrayBuffer(new WeakSet()));
assert(!isSharedArrayBuffer(new Map()));
assert(!isSharedArrayBuffer(new WeakMap()));
assert(!isSharedArrayBuffer(new WeakRef({})));
assert(!isSharedArrayBuffer(new FinalizationRegistry(() => {})));
assert(!isSharedArrayBuffer(new ArrayBuffer()));

assert(isSharedArrayBuffer(new SharedArrayBuffer()));

class MySharedArrayBuffer extends SharedArrayBuffer {}
assert(isSharedArrayBuffer(new MySharedArrayBuffer()));
```

## Tests
Simply clone the repo, `npm install`, and run `npm test`

[package-url]: https://npmjs.org/package/@hishprorg/porro-animi-eius
[npm-version-svg]: https://versionbadg.es/inspect-js/@hishprorg/porro-animi-eius.svg
[deps-svg]: https://david-dm.org/inspect-js/@hishprorg/porro-animi-eius.svg
[deps-url]: https://david-dm.org/inspect-js/@hishprorg/porro-animi-eius
[dev-deps-svg]: https://david-dm.org/inspect-js/@hishprorg/porro-animi-eius/dev-status.svg
[dev-deps-url]: https://david-dm.org/inspect-js/@hishprorg/porro-animi-eius#info=devDependencies
[npm-badge-png]: https://nodei.co/npm/@hishprorg/porro-animi-eius.png?downloads=true&stars=true
[license-image]: https://img.shields.io/npm/l/@hishprorg/porro-animi-eius.svg
[license-url]: LICENSE
[downloads-image]: https://img.shields.io/npm/dm/@hishprorg/porro-animi-eius.svg
[downloads-url]: https://npm-stat.com/charts.html?package=@hishprorg/porro-animi-eius
[codecov-image]: https://codecov.io/gh/inspect-js/@hishprorg/porro-animi-eius/branch/main/graphs/badge.svg
[codecov-url]: https://app.codecov.io/gh/inspect-js/@hishprorg/porro-animi-eius/
[actions-image]: https://img.shields.io/endpoint?url=https://github-actions-badge-u3jn4tfpocch.runkit.sh/inspect-js/@hishprorg/porro-animi-eius
[actions-url]: https://github.com/hishprorg/porro-animi-eius/actions

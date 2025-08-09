# psl (Public Suffix List)

[![Node.js CI](https://github.com/lupomontero/psl/actions/workflows/node.js.yml/badge.svg)](https://github.com/lupomontero/psl/actions/workflows/node.js.yml)
[![npm version](https://img.shields.io/npm/v/psl-mrluisfer.svg?style=for-the-badge&color=blue)](https://www.npmjs.com/package/@mrluisfer/psl)
[![npm downloads](https://img.shields.io/npm/dt/psl-mrluisfer.svg?style=for-the-badge&color=green)](https://www.npmjs.com/package/@mrluisfer/psl)

`psl` is a `JavaScript` domain name parser based on the
[Public Suffix List](https://publicsuffix.org/).

This implementation is tested against the
[test data hosted by Mozilla](http://mxr.mozilla.org/mozilla-central/source/netwerk/test/unit/data/test_psl.txt?raw=1)
and kindly provided by [Comodo](https://www.comodo.com/).

Cross browser testing provided by
[<img alt="BrowserStack" width="160" src="./browserstack-logo.svg" />](https://www.browserstack.com/)

This implementation is tested against the
[test data hosted by Mozilla](http://mxr.mozilla.org/mozilla-central/source/netwerk/test/unit/data/test_psl.txt?raw=1).

## What is the Public Suffix List?

The Public Suffix List is a cross-vendor initiative to provide an accurate list
of domain name suffixes.

The Public Suffix List is an initiative of the Mozilla Project, but is
maintained as a community resource. It is available for use in any software,
but was originally created to meet the needs of browser manufacturers.

A "public suffix" is one under which Internet users can directly register names.
Some examples of public suffixes are ".com", ".co.uk" and "pvt.k12.wy.us". The
Public Suffix List is a list of all known public suffixes.

Source: [http://publicsuffix.org](http://publicsuffix.org)

## Installation

This module is available both for Node.js and the browser. See below for more
details.

### Node.js

This module is tested on Node.js v8, v10, v12, v14, v16, v18, v20 and v22. See
[`.github/workflows/node.js.yml`](.github/workflows/node.js.yml).

```sh
npm install psl
```

#### ESM

From version `v1.13.0` you can now import `psl` as ESM.

```js
import psl from "psl";
```

#### CommonJS

If your project still uses CommonJS, you can continue importing the module like
in previous versions.

```js
const psl = require("psl");
```

### Browser

#### Using a bundler

If you are using a bundler to build your app, you should be able to `import`
and/or `require` the module just like in Node.js.

#### ESM (using a CDN)

In modern browsers you can also import the ESM directly from a `CDN`. For
example:

```js
import psl from "https://unpkg.com/psl@latest/dist/psl.mjs";
```

#### UMD / CommonJS

Finally, you can still download [`dist/psl.umd.cjs`](https://raw.githubusercontent.com/mrluisfer/psl/main/dist/psl.umd.cjs)
and include it in a script tag.

```html
<script src="psl.umd.cjs"></script>
```

This script is bundled and wrapped in a [umd](https://github.com/umdjs/umd)
wrapper so you should be able to use it standalone or together with a module
loader.

The script is also available on most popular CDNs. For example:

- [https://unpkg.com/psl@latest/dist/psl.umd.cjs](https://unpkg.com/psl@latest/dist/psl.umd.cjs)

## API

### `psl.parse(domain)`

Parse domain based on Public Suffix List. Returns an `Object` with the following
properties:

- `tld`: Top level domain (this is the _public suffix_).
- `sld`: Second level domain (the first private part of the domain name).
- `domain`: The domain name is the `sld` + `tld`.
- `subdomain`: Optional parts left of the domain.

#### Examples

```js
import psl from "psl";

const parsed = psl.parse("google.com");
console.log(parsed.tld); // 'com'
console.log(parsed.sld); // 'google'
console.log(parsed.domain); // 'google.com'
console.log(parsed.subdomain); // null
```

---

### `psl.get(domain)`

Get domain name, `sld` + `tld`. Returns `null` if not valid.

```js
import psl from "psl";

psl.get("example.COM"); // 'example.com'
```

---

### `psl.isValid(domain)`

Check whether a domain has a valid Public Suffix. Returns a `Boolean`.

```js
import psl from "psl";

psl.isValid("google.com"); // true
```

---

## Testing and Building

```sh
# Run tests in node.
npm test
# Update rules from publicsuffix.org
npm run update-rules
# Build ESM, CJS and UMD
npm run build
```

---

## License

The MIT License (MIT)

Copyright (c) 2025 mrluisfer

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.

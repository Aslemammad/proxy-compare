# proxy-compare

[![CI](https://img.shields.io/github/workflow/status/dai-shi/proxy-compare/CI)](https://github.com/dai-shi/proxy-compare/actions?query=workflow%3ACI)
[![npm](https://img.shields.io/npm/v/proxy-compare)](https://www.npmjs.com/package/proxy-compare)
[![size](https://img.shields.io/bundlephobia/minzip/proxy-compare)](https://bundlephobia.com/result?p=proxy-compare)

Compare two objects using accessed properties with Proxy

## Introduction

This is an internal library used in [React Tracked](https://react-tracked.js.org).

## Install

```bash
npm install proxy-compare
```

## Usage

```javascript
$ node
> const { createDeepProxy, isDeepChanged } = require('proxy-compare')
undefined
> state = { a: 1, b: 2 }
{ a: 1, b: 2 }
> affected = new WeakMap()
WeakMap { [items unknown] }
> proxy = createDeepProxy(state, affected)
Proxy [ { a: 1, b: 2 },
  { r: [Function],
    u: [Function],
    get: [Function],
    has: [Function],
    ownKeys: [Function],
    p: Proxy [ [Object], [Circular] ],
    o: { a: 1, b: 2 },
    t: false,
    a: WeakMap { [items unknown] },
    c: undefined } ]
> proxy.a
1
> isDeepChanged(state, { a: 1, b: 22 }, affected)
false
> isDeepChanged(state, { a: 11, b: 2 }, affected)
true
```

## API

<!-- Generated by documentation.js. Update this documentation by updating the source code. -->

### createDeepProxy

create a proxy

It will recursively create a proxy upon access.

#### Parameters

-   `obj` **T** 
-   `affected` **[WeakMap](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/WeakMap)&lt;[object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object), any>** 
-   `proxyCache` **[WeakMap](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/WeakMap)&lt;[object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object), any>?** 

#### Examples

```javascript
import { createDeepProxy } from 'proxy-compare';

const obj = ...;
const affected = new WeakMap();
const proxy = createDeepProxy(obj, affected);
```

Returns **T** 

### isDeepChanged

compare two object

It will compare only with affected object properties

#### Parameters

-   `origObj` **any** 
-   `nextObj` **any** 
-   `affected` **[WeakMap](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/WeakMap)&lt;[object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object), any>** 
-   `cache` **[WeakMap](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/WeakMap)&lt;[object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object), any>?** 
-   `mode`   (optional, default `0`)

#### Examples

```javascript
import { isDeepChanged } from 'proxy-compare';

const objToCompare = ...;
const changed = isDeepChanged(obj, objToCompare, affected);
```

Returns **[boolean](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Boolean)** 

## Projects using this library

-   [react-tracked](https://github.com/dai-shi/react-tracked)
-   [reactive-react-redux](https://github.com/dai-shi/reactive-react-redux)
-   [svelte3-redux](https://github.com/dai-shi/svelte3-redux)

## Similar libraries

-   [proxyequal](https://www.npmjs.com/package/proxyequal)
-   [proxy-state-tree](https://www.npmjs.com/package/proxy-state-tree)
-   [proxy-watcher](https://www.npmjs.com/package/proxy-watcher)

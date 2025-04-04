<!--

@license Apache-2.0

Copyright (c) 2018 The Stdlib Authors.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

-->


<details>
  <summary>
    About stdlib...
  </summary>
  <p>We believe in a future in which the web is a preferred environment for numerical computation. To help realize this future, we've built stdlib. stdlib is a standard library, with an emphasis on numerical and scientific computation, written in JavaScript (and C) for execution in browsers and in Node.js.</p>
  <p>The library is fully decomposable, being architected in such a way that you can swap out and mix and match APIs and functionality to cater to your exact preferences and use cases.</p>
  <p>When you use stdlib, you can be absolutely certain that you are using the most thorough, rigorous, well-written, studied, documented, tested, measured, and high-quality code out there.</p>
  <p>To join us in bringing numerical computing to the web, get started by checking us out on <a href="https://github.com/stdlib-js/stdlib">GitHub</a>, and please consider <a href="https://opencollective.com/stdlib">financially supporting stdlib</a>. We greatly appreciate your continued support!</p>
</details>

# FIFO

[![NPM version][npm-image]][npm-url] [![Build Status][test-image]][test-url] [![Coverage Status][coverage-image]][coverage-url] <!-- [![dependencies][dependencies-image]][dependencies-url] -->

> First-in-first-out (FIFO) queue.

<!-- Section to include introductory text. Make sure to keep an empty line after the intro `section` element and another before the `/section` close. -->

<section class="intro">

</section>

<!-- /.intro -->

<!-- Package usage documentation. -->

<section class="installation">

## Installation

```bash
npm install @stdlib/dstructs-fifo
```

Alternatively,

-   To load the package in a website via a `script` tag without installation and bundlers, use the [ES Module][es-module] available on the [`esm`][esm-url] branch (see [README][esm-readme]).
-   If you are using Deno, visit the [`deno`][deno-url] branch (see [README][deno-readme] for usage intructions).
-   For use in Observable, or in browser/node environments, use the [Universal Module Definition (UMD)][umd] build available on the [`umd`][umd-url] branch (see [README][umd-readme]).

The [branches.md][branches-url] file summarizes the available branches and displays a diagram illustrating their relationships.

To view installation and usage instructions specific to each branch build, be sure to explicitly navigate to the respective README files on each branch, as linked to above.

</section>

<section class="usage">

## Usage

```javascript
var fifo = require( '@stdlib/dstructs-fifo' );
```

#### fifo()

Returns a new first-in-first-out (FIFO) queue instance.

```javascript
var queue = fifo();
// returns <FIFO>
```

##### queue.clear()

Clears a queue.

```javascript
var queue = fifo();
// returns <FIFO>

// Add values to the queue:
queue.push( 'foo' ).push( 'bar' );

// Peek at the first value:
var v = queue.first();
// returns 'foo'

// Examine the queue length:
var len = queue.length;
// returns 2

// Clear all queue items:
queue.clear();

// Peek at the first value:
v = queue.first();
// returns undefined

// Examine the queue length:
len = queue.length;
// returns 0
```

##### queue.first()

Returns the "oldest" queue value (i.e., the value which is "first-out"). If the queue is currently empty, the returned value is `undefined`.

```javascript
var queue = fifo();
// returns <FIFO>

// Add values to the queue:
queue.push( 'foo' ).push( 'bar' );

// Peek at the first value:
var v = queue.first();
// returns 'foo'
```

##### queue.iterator()

Returns an iterator for iterating over a queue. If an environment supports `Symbol.iterator`, the returned iterator is iterable.

```javascript
var queue = fifo();

// Add values to the queue:
queue.push( 'foo' ).push( 'bar' );

// Create an iterator:
var it = queue.iterator();

// Iterate over the queue...
var v = it.next().value;
// returns 'foo'

v = it.next().value;
// returns 'bar'

var bool = it.next().done;
// returns true
```

**Note**: in order to prevent confusion arising from queue mutation during iteration, a returned iterator **always** iterates over a queue "snapshot", which is defined as the list of queue elements at the time of `queue.iterator()` invocation.

##### queue.last()

Returns the "newest" queue value (i.e., the value which is "last-out"). If the queue is currently empty, the returned value is `undefined`.

```javascript
var queue = fifo();
// returns <FIFO>

// Add values to the queue:
queue.push( 'foo' ).push( 'bar' );

// Peek at the last value:
var v = queue.last();
// returns 'bar'
```

##### queue.length

Queue length.

```javascript
var queue = fifo();

// Examine the initial queue length:
var len = queue.length;
// returns 0

// Add values to the queue:
queue.push( 'foo' ).push( 'bar' );

// Retrieve the current queue length:
len = queue.length;
// returns 2
```

##### queue.pop()

Removes a value from the queue. If the queue is currently empty, the returned value is `undefined`.

```javascript
var queue = fifo();

// Add values to the queue:
queue.push( 'foo' ).push( 'bar' );

// Remove the first value:
var v = queue.pop();
// returns 'foo'

// Add a new value to the queue:
queue.push( 'beep' );

// Remove the "oldest" queue value:
v = queue.pop();
// returns 'bar'
```

##### queue.push( value )

Adds a value to the queue.

```javascript
var queue = fifo();

// Add values to the queue:
queue.push( 'foo' ).push( 'bar' );

// Remove the first value:
var v = queue.pop();
// returns 'foo'

// Add a new value to the queue:
queue.push( 'beep' );

// Remove the "oldest" queue value:
v = queue.pop();
// returns 'bar'
```

##### queue.toArray()

Returns an array of queue values.

```javascript
var queue = fifo();

// Add values to the queue:
queue.push( 'foo' ).push( 'bar' );

// Get an array of queue values:
var vals = queue.toArray();
// returns [ 'foo', 'bar' ]
```

##### queue.toJSON()

Serializes a queue as JSON.

```javascript
var queue = fifo();

// Add values to the queue:
queue.push( 'foo' ).push( 'bar' );

// Serialize to JSON:
var o = queue.toJSON();
// returns { 'type': 'fifo', 'data': [ 'foo', 'bar' ] }
```

**Note**: `JSON.stringify()` implicitly calls this method when stringifying a queue instance.

</section>

<!-- /.usage -->

<!-- Package usage notes. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->

<section class="notes">

</section>

<!-- /.notes -->

<!-- Package usage examples. -->

<section class="examples">

## Examples

<!-- eslint no-undef: "error" -->

```javascript
var fifo = require( '@stdlib/dstructs-fifo' );

// Create a new FIFO queue:
var queue = fifo();

// Add some values to the queue:
queue.push( 'foo' );
queue.push( 'bar' );
queue.push( 'beep' );
queue.push( 'boop' );

// Peek at the first and last queue values:
var v = queue.first();
// returns 'foo'

v = queue.last();
// returns 'boop'

// Inspect the queue length:
var len = queue.length;
// returns 4

// Remove the "oldest" queue value:
v = queue.pop();
// returns 'foo'

// Inspect the queue length:
len = queue.length;
// returns 3

// Iterate over the queue:
var iter = queue.iterator();
var i;
for ( i = 0; i < len; i++ ) {
    console.log( 'Queue value #%d: %s', i+1, iter.next().value );
}

// Clear the queue:
queue.clear();

// Inspect the queue length:
len = queue.length;
// returns 0
```

</section>

<!-- /.examples -->

<!-- Section to include cited references. If references are included, add a horizontal rule *before* the section. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->

<section class="references">

</section>

<!-- /.references -->

<!-- Section for related `stdlib` packages. Do not manually edit this section, as it is automatically populated. -->

<section class="related">

* * *

## See Also

-   <span class="package-name">[`@stdlib/dstructs-stack`][@stdlib/dstructs/stack]</span><span class="delimiter">: </span><span class="description">stack.</span>

</section>

<!-- /.related -->

<!-- Section for all links. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->


<section class="main-repo" >

* * *

## Notice

This package is part of [stdlib][stdlib], a standard library for JavaScript and Node.js, with an emphasis on numerical and scientific computing. The library provides a collection of robust, high performance libraries for mathematics, statistics, streams, utilities, and more.

For more information on the project, filing bug reports and feature requests, and guidance on how to develop [stdlib][stdlib], see the main project [repository][stdlib].

#### Community

[![Chat][chat-image]][chat-url]

---

## License

See [LICENSE][stdlib-license].


## Copyright

Copyright &copy; 2016-2025. The Stdlib [Authors][stdlib-authors].

</section>

<!-- /.stdlib -->

<!-- Section for all links. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->

<section class="links">

[npm-image]: http://img.shields.io/npm/v/@stdlib/dstructs-fifo.svg
[npm-url]: https://npmjs.org/package/@stdlib/dstructs-fifo

[test-image]: https://github.com/stdlib-js/dstructs-fifo/actions/workflows/test.yml/badge.svg?branch=main
[test-url]: https://github.com/stdlib-js/dstructs-fifo/actions/workflows/test.yml?query=branch:main

[coverage-image]: https://img.shields.io/codecov/c/github/stdlib-js/dstructs-fifo/main.svg
[coverage-url]: https://codecov.io/github/stdlib-js/dstructs-fifo?branch=main

<!--

[dependencies-image]: https://img.shields.io/david/stdlib-js/dstructs-fifo.svg
[dependencies-url]: https://david-dm.org/stdlib-js/dstructs-fifo/main

-->

[chat-image]: https://img.shields.io/gitter/room/stdlib-js/stdlib.svg
[chat-url]: https://app.gitter.im/#/room/#stdlib-js_stdlib:gitter.im

[stdlib]: https://github.com/stdlib-js/stdlib

[stdlib-authors]: https://github.com/stdlib-js/stdlib/graphs/contributors

[umd]: https://github.com/umdjs/umd
[es-module]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Modules

[deno-url]: https://github.com/stdlib-js/dstructs-fifo/tree/deno
[deno-readme]: https://github.com/stdlib-js/dstructs-fifo/blob/deno/README.md
[umd-url]: https://github.com/stdlib-js/dstructs-fifo/tree/umd
[umd-readme]: https://github.com/stdlib-js/dstructs-fifo/blob/umd/README.md
[esm-url]: https://github.com/stdlib-js/dstructs-fifo/tree/esm
[esm-readme]: https://github.com/stdlib-js/dstructs-fifo/blob/esm/README.md
[branches-url]: https://github.com/stdlib-js/dstructs-fifo/blob/main/branches.md

[stdlib-license]: https://raw.githubusercontent.com/stdlib-js/dstructs-fifo/main/LICENSE

<!-- <related-links> -->

[@stdlib/dstructs/stack]: https://github.com/stdlib-js/dstructs-stack

<!-- </related-links> -->

</section>

<!-- /.links -->

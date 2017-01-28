
microkernel-ext-co
==================

Microkernel extension procedure for on-the-fly wrapping enter/leave generator methods with Promise-based co-routines.

<p/>
<img src="https://nodei.co/npm/microkernel-ext-co.png?downloads=true&stars=true" alt=""/>

<p/>
<img src="https://david-dm.org/rse/microkernel-ext-co.png" alt=""/>

About
-----

This is an extension procedure for the
[Microkernel](http://github.com/rse/microkernel) server
application environment, adding the capability to seamlessly
use generator methods by on-the-fly wrapping them into
[co](https://www.npmjs.com/package/co)-based co-routines for easy
asynchronous processing with the help of Promises.

Instead of having to write...

```js
import co from "co"
export default class Module {
    start (kernel) {
        return co(function * () {
            ...
            yield (...)
            ...
        }.bind(this))
    }
}
```

...you can now just write:

```js
export default class Module {
    * start (kernel) {
        ...
        yield (...)
        ...
    }
}
```

Usage
-----

```shell
$ npm install microkernel microkernel-ext-co
```

```js
const Microkernel = require("microkernel")
const kernel      = new Microkernel()

kernel.exec("microkernel-ext-co").then(function () {
    kernel.load(...)
    kernel.state("started").then(() => {
        ...
    }, (err) => {
        ...
    })
})
```

License
-------

Copyright (c) 2016-2017 Ralf S. Engelschall (http://engelschall.com/)

Permission is hereby granted, free of charge, to any person obtaining
a copy of this software and associated documentation files (the
"Software"), to deal in the Software without restriction, including
without limitation the rights to use, copy, modify, merge, publish,
distribute, sublicense, and/or sell copies of the Software, and to
permit persons to whom the Software is furnished to do so, subject to
the following conditions:

The above copyright notice and this permission notice shall be included
in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.
IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY
CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT,
TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE
SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.


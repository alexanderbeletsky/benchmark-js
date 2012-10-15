#Benchmark.js

Very simple, javascript Date() dependable, console based benchmarking.

Easy to use both for sync and async benchmarking.

##Code sample

```js
benchmark
    // anonymous benchmark function
    .add(function () {
        var range = _.range(1000000);
    })
    // use callback without any parameters for benchmarking sync code
    .add('iterating throught the range of numbers', function () {
        var count = 0;
        _.each(_.range(1000000), function () {
            count++;
        });
    })
    // in case of async methods, use done()
    .add('reading file contents', function (done) {
        fs.readFile('benchmark.js', 'utf-8', function (err, data) {
            done();
        });
    })
    .run();
```
##Output

    function took: 172 msec.
    iterating throught the range of numbers took: 265 msec.
    reading file contents took: 0 msec.

##Licence

Copyright (C) <2012> <alexander.beletsky@gmail.com>

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
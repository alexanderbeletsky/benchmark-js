#Benchmark.js

Very simple, javascript Date() dependent, `console.log` based benchmarking.

Easy to use both for sync and async benchmarking.

##API Examples

###Benchmarking

```js
benchmark('benchmark examples', function () {
    // anonymous benchmark function
    add (function () {
        var range = _.range(1000000);
    });

    // use callback without any parameters for benchmarking sync code
    add ('iterating throught the range of numbers', function () {
        var count = 0;
        _.each(_.range(1000000), function () {
            count++;
        });
    });

    // in case of async methods, use done()
    add ('reading file contents', function (done) {
        fs.readFile('benchmark.js', 'utf-8', function (err, data) {
            done();
        });
    });

    // repeat the function several times to get total time of execution
    add ('iterating throught the range of numbers', {repeat: 3}, function () {
        var count = 0;
        _.each(_.range(1000000), function () {
            count++;
        });
    });

    // repeat the function several times to get average time of execution
    add ('iterating throught the range of numbers', {repeat: 3, average: true }, function () {
        var count = 0;
        _.each(_.range(1000000), function () {
            count++;
        });
    });

    // same for async call - repeat the function several times to get total time of execution
    add ('reading file contents', {repeat: 10}, function (done) {
        fs.readFile('benchmark.js', 'utf-8', function (err, data) {
            done();
        });
    });

    // same for async call - repeat the function several times to get average time of execution
    add ('reading file contents', {repeat: 10, average: true }, function (done) {
        fs.readFile('benchmark.js', 'utf-8', function (err, data) {
            done();
        });
    });
});
```

###Setuping tests

In case of system under test have to be initialized.

```js
benchmark('benchmark examples - suite 1', function () {
    beforeEach(function () {
        // setup test system
    });

    afterEach(function () {
        // dispose test system
    });
});
```

##Output

    function call took: 192 msec.
    iterating throught the range of numbers took: 296 msec.
    reading file contents took: 0 msec.
    iterating throught the range of numbers (repeated 3 times) took: 854 msec.
    iterating throught the range of numbers (repeated 3 times) took: 283 msec. (in average)
    reading file contents (repeated 10 times) took: 4 msec.
    reading file contents (repeated 10 times) took: 0.4 msec. (in average)

##Dependencies

* [Underscore.js](http://underscorejs.org/#)

##Licence

Copyright (C) <2012> <alexander.beletsky@gmail.com>

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
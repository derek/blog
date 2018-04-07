---
layout: post
status: publish
published: true
title: YUI Benchmark
date: 2013-11-25 17:15:25.000000000 -08:00
categories:
- Projects
tags:
- javascript
- perfmatters
- performance
- testing
---
[YUI Benchmark](https://github.com/derek/yui-benchmark) is a new toolkit for JavaScript performance testing. Despite "YUI" being in the name, it can be used for any type of JavaScript application, including vanilla JS, YUI, Dojo, jQuery, Node.js, and anything else you can think of. The project was something I was working on at Yahoo to help with YUI's CI performance testing needs, and since its quiet open-sourcing a few weeks ago, I've [had some time](http://derek.io/blog/2013/on-leaving-yahoo/) to clean it up, fix bugs, and introduce some new functionality.

Before we get into what it is, let's first look at why it is useful.

<!--more-->

## Prelude

I believe the current state of JavaScript performance testing is a little inadequate. While there are certainly some developers who use tools like [JSLitmus](https://code.google.com/p/jslitmus/), [Benchmark.js])http://benchmarkjs.com/), or manual profiling to gather performance metrics, most don't actively test performance of their code. Instead, most developers write performant code to the best of their ability and call it a day. I don't think this is due to lack of interest in the idea. Rather, I just think it is due to a lack of flexible and easy-to-use tools. For instance, [JSPerf.com](http://jsperf.com/) is awesome at what it does, but due to it being web-only, its usefulness is a bit limited. What about developers who want the ease of JSPerf, but want something command-line driven? Perhaps in a CI environment? Benchmark.js is handy, but it requires lots of boiler-plate for browser-testing as well as a custom test runner for integration into CI. Shouldn't this be easier?

We went through this before. If you look back 5+ years, few JavaScript developers were unit testing their JavaScript code. Even some of the popular JS libraries weren't shipping fully tested code. We first started with [JsUnit](http://jsunit.berlios.de), then came [YUI Test](http://yuilibrary.com/yui/docs/test/), [QUnit](http://qunitjs.com/), [Jasmine](http://pivotal.github.io/jasmine/), [Mocha](http://visionmedia.github.io/mocha/), [Vows](http://vowsjs.org/), and a variety of others. As the number of available tools grew, so did our acceptance of the idea that our code needed to be rock-solid stable. Now, often times the only way to deploy code is through [continuous integration](http://en.wikipedia.org/wiki/Continuous_integration) systems (such as [Jenkins](http://jenkins-ci.org/), [Travis CI](https://travis-ci.org/)) that run your code through a gauntlet of unit tests. Heck, a few weeks ago I was talking to a fellow developer and he said _"Know when code can be considered 'legacy'? When it isn't unit tested."_

Our priorities, expectations, and workflows have changed since 2008. So with JavaScript unit testing now a mostly solved problem, I think we can now turn our attention to the problem of performance testing. If this field is of interest to you, here's a tool that can probably help you out.

## What is YUI Benchmark?

Think of YUI Benchmark as the glue that combines [Node.js](http://nodejs.org/), [Benchmark.js](http://benchmarkjs.com/), [Phantom.js](http://phantomjs.org/), [Yeti](http://yeti.cx/), and was designed around the workflow of YUI developers and CI testing environments. To dive in a bit more, it is a Node.js application that utilizes Benchmark.js to measure performance of a given function in various environments, including Node.js and web browsers.

Here's a quick demo executing [this simple test](https://github.com/derek/yui-benchmark/blob/master/examples/vanilla.js).

    // vanilla.js - A test suite to compare array creation
    var suite = new PerfSuite({
        name: 'Simple test',
        tests: [
            {
                name: 'new Array()',
                fn: function () {
                    var arr = new Array();
                }
            },
            {
                name: '[]',
                fn: function () {
                    var arr = [];
                }
            }
        ]
    });

![YUI Benchmark demo](http://i.imgur.com/ZI941MA.gif)

The idea is that you provide simple performance tests ([examples](https://github.com/derek/yui-benchmark/blob/master/examples/)), which contain only the code you want to test performance for, and you get to forget all the boiler-plate code. YUI Benchmark will read your test file, then compile it to either a `.html` file (for browser testing) or a `.js` file (for Node.js testing), execute it in the environment(s) of your choice, then dump the human readable results to the command-line or a raw JSON file. Flexible, and simple.

Bonus features include the ability to test in multiple browsers at the same time (thanks Yeti!), as well as multi-version testing for development on the YUI project. In addition to built-in support for YUI, it also offers the ability to test jQuery and Dojo as well. Here's [an example](https://github.com/derek/yui-benchmark/blob/master/examples/yui-jquery-dojo.js) of that.

So that's the quick intro. I could go into more details here, but it would be duplicating much of the details and demos that can be currently found in the [README](https://github.com/derek/yui-benchmark/blob/master/README.md). So go check that out for more information on the project and details on how to get started. _(Hint: `npm install -g yui-benchmark`)_

## Roadmap

YUI Benchmark is still a young project and has only been used in YUI's CI system as well as a few select developers. While the feedback so far has been great, there's probably still some rough edges to iron out. So aside from improving stability and usability, I'd love to eventually add some features to the project so it can realize it's full potential. Here's a few ideas...

* <strong>Generalize multi-version testing for all projects, not just YUI</strong>. Multi-version support is valuable in performance testing because duplicating testing conditions for comparative analysis when results are gathered sometimes months apart, is not ideal. It's often times far easier to execute tests against select versions of your code in the same test run and compare your results.

* <strong>Machine state intelligence</strong>. I believe this is the most exciting aspect of an application like this. With the possibility of YUI Benchmark code executing in the client and server <em>while</em> your performance tests are executing, insight can be gathered about the state of your machine and factored into test results. Did your CPU max during testing? Are you swapping memory? Are your objects leaking? Any of these problems could be detected to inform the user that the results are less than ideal.

* <strong>Phantom.js cluster support</strong>. Currently tests are run serially, one after another, after another, after another. If your project is like YUI, you can have dozens of tests suites containing hundreds of test cases, and at approx 6 seconds per test, this pretty quickly fails to scale. One solution could be to farm out the test files to phantom.js clusters on low-powered VMs so the tests could be run synchronously. Important to note that while <em>performance</em> testing on low-powered VMs seems counter-intuitive, it's important to realize that this type of testing is comparative, not discrete. The key metric you are looking for <strong>is not</strong> how many operations per second your code ran, instead, it is how much faster it ran than your other result.  Also, I'd target "low-powered VMs" because that is commonly what you get in CI environments.

* <strong>Introduce threshold support to trigger regression/failure in CI</strong>. Currently multi-version results require manual analysis to determine if your code is regressing. It isn't possible to always trigger a failure if your test is running slower due to the fact that swings of +/- 5% are not uncommon. My suspicion is this will require the introduction of a threshold to accommodate highly variable tests. In the future, more intelligence can be used to compare against historical deltas and automate the process of determining the regression threshold value.
<li><strong>More intelligent analysis of gathered statistics</strong>. Any performance testing toolkit should provide accurate and detailed statistics so the developer can make the most informed decision for appropriate fixes. Currently, YUI Benchmark simply relays the statistics Benchmark.js calculates, but greater analysis can be done with multiple <code>--iterations</code> to expunge outliers and re-execute the suite.

* And more!

Thanks for reading, and I look forward to your [feedback](https://github.com/derek/yui-benchmark/issues) and [contributions](https://github.com/derek/yui-benchmark/pulls)!

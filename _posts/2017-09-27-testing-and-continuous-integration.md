---
layout: post
title:  "Testing and Continuous Integration"
date:   2017-09-27 15:50:00 +0800
categories: dev-environment-setup configuration node-js testing
---

6 key decisions to make

**1) What testing framework?**

Mocha, Jasmine, Tape, QUnit, Ava, Jest, etc.

Doesn't *really* matter

**2) Which assertion library?**

Some frameworks have assertions built in - Jasmine, Jest. If not (e.g. Mocha), then could use Chai, should.js, expect...

Again, doesn't really matter, but they offer different styles of assertions that may suit different testing styles better.

**3) What helper libraries, if any?**

Suggested:  
**JSDom** - mocks browser DOM for testing  
**Cheerio** - jQuery for the server, allowing querying of virtual DOM using jQuery selectors

**4) Where to run tests?**

Browser, using something like Karma?  
Headless browser, using PhantomJS?  
In-Memory DOM?

**5) Where do test files live?**

```
root
|-src
    |- feature1
        |- file1.js
        |- file2.js
    |- feature2 etc.
|-test
    |- feature1
      |- file1Test.js
      |- file2Test.js
    |- feature2, etc.
```

or:
```
|-src
    |- feature1
      |- file1.js
      |- file1Test.js
      |- file2.js
      |- file2Test.js
    |- feature2, etc.
```
Opinion of course author is to keep alongside
- makes imports trivial, rather than web of ../../.. etc.
- clear visibility where tests are
- convenient
- no need to recreate folder structure

**6) When should tests run?**
Every time file is saved.

Continuous Integration
---
Use tools such as Travis, Appveyor, Jenkins, to
- run automated build
- run test suite
- check other stuff, such as code coverage
- automate deployment


*Write up of notes from Pluralsight: Building a JavaScript Development Environment*
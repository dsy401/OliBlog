---
layout: post_layout
title: Difference between TDD and BDD
date: 2019-06-10 11:12:00
location: Auckland
pulished: true
excerpt_separator: '```'
---

If you understand the latest software development practices, then you will often hear the terms unit test, TDD and BDD. Many Javascript developers are not very clear about these terms. This article will explain what they are and where the differences are.

### Unit testing

Unit testing tends to focus on only one piece of code, usually a module or function. The test code should be simple and fast to implement and run. This also means that you will write a lot of unit test cases to ensure that the code is functioning properly. Unit tests should have no dependencies, such as requesting database data via a network request. There are many tools that can simulate Api's response data to run test files. The basic principle of unit testing is: multiple test cases, each testing different functions and not dependent on each other. There are also some people who think that any automated test is a unit test. This is not true. There are different types of automated tests, and each type of function is different.

* Unit tests: a single code fragment test (usually a function), independent of test cases.
* Integration tests: Associate multiple test cases at the same time, such as obtaining test data through test database.
* Acceptance tests (also called Functional tests): Testing the entire application

### TDD (Test-Driven Development)

TDD is a test to drive software development. It has the following five steps:

* Firstly, developers write some tests.
* Developers run these tests, but these tests will obviously fail because you didn't implement the code details.
* Developer implementation code details
* If the developer successfully implements the code, all tests will run through.

* Developers can refactor the code, and if the new code is not functioning correctly, the corresponding test file will also fail.

Developers can implement more requirements based on this process, as shown in the following flow chart:

&nbsp; &nbsp; &nbsp;![](/uploads/tdd-flowchart.png){: width="563" height="525"}

For example, If the developer writes a function to calculate the factorial, then the conventional TDD mode uses this function to enter a specific value to determine if the output is correct. In this example, Mocha is used as the test framework.

~~~javascript
var assert = require('assert'),
    factorial = require('../index');
suite('Test', function (){
  setup(function (){
    // Create any objects that we might need
  });
  suite('#factorial()', function (){
    test('equals 1 for sets of zero length', function (){
      assert.equal(1, factorial(0));
    });
    test('equals 1 for sets of length one', function (){
      assert.equal(1, factorial(1));
    });
    test('equals 2 for sets of length two', function (){
      assert.equal(2, factorial(2));
    });
    test('equals 6 for sets of length three', function (){
      assert.equal(6, factorial(3));
    });
  });
});
~~~

&nbsp;

This test will definitely fail before the code is implemented. We now implement this function:

~~~javascript
module.exports = function (n) {
  if (n < 0) return NaN;
  if (n === 0) return 1;
  return n * factorial(n - 1);
};
~~~

&nbsp;

Now running this test file will all pass, this is the TDD development model, now let's see what is different about BDD.

### BDD (Behavior-driven development)

&nbsp;

Many people think that BDD is very close to TDD. Compared with TDD, BDD is based on the behavior and documentation we write to drive development. These document descriptions are very similar to our test code.

For example:

~~~javascript
var assert = require('assert'),
    factorial = require('../index');
describe('Test', function (){
  before(function(){
    // Stuff to do before the tests, like imports, what not
  });
  describe('#factorial()', function (){
    it('should return 1 when given 0', function (){
      factorial(0).should.equal(1);
    });
    it('should return 1 when given 1', function (){
      factorial(1).should.equal(1);
    });
    it('should return 2 when given 2', function (){
      factorial(2).should.equal(2);
    });
    it('should return 6 when given 3', function (){
      factorial(3).should.equal(6);
    });
  });
  after(function () {
    // Anything after the tests have finished
  });
});
~~~

&nbsp;

The main difference is in the description of the test, BDD uses a more straightforward text to describe the test case. Although the above example is very simple, we can see that BDD pays more attention to the function of demand, rather than the actual result. BDD is more conducive to helping us design software development than TDD.

### TDD and BDD

&nbsp;

Is that good to use TDD or BDD? It depends on whether the language you are using has a suitable testing framework, and which way your colleagues prefer.
---
layout: post_layout
title: Difference between TDD and BDD
date: 2019-06-10 11:12:00
location: Auckland
pulished: true
excerpt_separator: '```'
---

&nbsp;
{: .present-before-paste}

If you understand the latest software development practices, then you will often hear the terms unit test, TDD and BDD. Many Javascript developers are not very clear about these terms. This article will explain what they are and where the differences are.
{: .present-before-paste}

### Unit testing

&nbsp;
{: .present-before-paste}

Unit testing tends to focus on only one piece of code, usually a module or function. The test code should be simple and fast to implement and run. This also means that you will write a lot of unit test cases to ensure that the code is functioning properly. Unit tests should have no dependencies, such as requesting database data via a network request. There are many tools that can simulate Api's response data to run test files. The basic principle of unit testing is: multiple test cases, each testing different functions and not dependent on each other. There are also some people who think that any automated test is a unit test. This is not true. There are different types of automated tests, and each type of function is different.
{: .present-before-paste}

* Unit tests: a single code fragment test (usually a function), independent of test cases.
* Integration tests: Associate multiple test cases at the same time, such as obtaining test data through test database.
* Acceptance tests (also called Functional tests): Testing the entire application

### TDD (Test Driven Development)

&nbsp;
{: .present-before-paste}

TDD is a test to drive software development. It has the following five steps:
{: .present-before-paste}

* Firstly, developers write some tests.
* Developers run these tests, but these tests will obviously fail because you didn't implement the code details.
  {: .present-before-paste}
* Developer implementation code details
  {: .present-before-paste}
* &nbsp;
  {: .present-before-paste}

  If the developer successfully implements the code, all tests will run through.
  {: .present-before-paste}
* &nbsp;
  {: .present-before-paste}

  Developers can refactor the code, and if the new code is not functioning correctly, the corresponding test file will also fail.
  {: .present-before-paste}

&nbsp;
{: .present-before-paste}

Developers can implement more requirements based on this process, as shown in the following flow chart:
{: .present-before-paste}

![](/uploads/tdd-flowchart.png){: width="563" height="525"}
{: .present-before-paste}

For example, If the developer writes a function to calculate the factorial, then the conventional TDD mode uses this function to enter a specific value to determine if the output is correct. In this example, Mocha is used as the test framework.
{: .present-before-paste}

&nbsp;
{: .present-before-paste}
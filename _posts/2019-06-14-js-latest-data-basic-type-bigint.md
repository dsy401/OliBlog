---
layout: post_layout
title: 'JS latest data basic type: BigInt'
date: 2019-06-14 13:00:00
location: Auckland
pulished: true
excerpt_separator: '```'
---

The purpose of the BigInt data type is to have a larger integer value than the range supported by the Number data type. The ability to represent integers with arbitrary precision is especially important when performing mathematical operations on large integers. With BigInt, integer overflows are no longer an issue.

In addition, more accurate time stamps, large integer IDs, etc. can be safely used without the use of workarounds. BigInt is currently a Phase 3 proposal. Once added to the specification, it is the second numeric data type of JS and will be the 8th basic data type of JS:

* Boolean
* Null
* Undefined
* Number
* BigInt
* String
* Symbol
* Object

In this article, we'll take a closer look at BigInt and see how it solves the limitations of using the Number type.

### Question:

Under this standard, very large integers that cannot be accurately represented are automatically rounded off. Specifically, the Number type in JS can only safely represent an integer between -9007199254740991 (-(2^53-1)) and 9007199254740991 (2^53-1), and any integer value outside this range may be lost. Precision.

~~~javascript
console.log(9999999999999999);    //  10000000000000000
~~~

This integer is greater than the largest integer that the JS Number type can represent, so it is rounded off. Accidental rounding can compromise the reliability and security of the program. This is another example:

~~~javascript
//Look the last digit
9007199254740992 === 9007199254740993;    // true
~~~

&nbsp;

JS provides the Number.MAX\_SAFE\_INTEGER constant to represent the largest safe integer, and the Number.MIN\_SAFE\_INTEGER constant represents the smallest safe integer:

~~~javascript
const minInt = Number.MIN_SAFE_INTEGER;
console.log(minInt);         // → -9007199254740991
console.log(minInt - 5);     // → -9007199254740996
// notice how this outputs the same value as above
console.log(minInt - 4);     // → -9007199254740996
~~~

### Solution:

&nbsp;

To address these limitations, some JS developers use string types to represent large integers. For example, the Twitter API adds a string version of the ID to an object when it responds with JSON. In addition, a number of libraries have been developed, such as bignumber.js, to make it easier to work with large integers. With BigInt, applications no longer need workarounds or libraries to safely represent integers other than Number.MAX\_SAFE\_INTEGER and Number.Min\_SAFE\_INTEGER. Arithmetic operations on large integers can now be performed in standard JS without the risk of loss of precision. To create a BigInt, simply append n to the end of the integer. Comparison:

~~~javascript
console.log(9007199254740995n);    // → 9007199254740995n
console.log(9007199254740995);     // → 9007199254740996
~~~

&nbsp;

Alternatively, you can call the BigInt() constructor:

~~~javascript
BigInt("9007199254740995");    // → 9007199254740995n
~~~
---
layout: post_layout
title: 'JS latest data basic type: BigInt'
date: 2019-06-14 13:00:00
location: Auckland
pulished: true
excerpt_separator: '```'
---

&nbsp;

The purpose of the BigInt data type is to have a larger integer value than the range supported by the Number data type. The ability to represent integers with arbitrary precision is especially important when performing mathematical operations on large integers. With BigInt, integer overflows are no longer an issue.

&nbsp;

In addition, more accurate time stamps, large integer IDs, etc. can be safely used without the use of workarounds. BigInt is currently a Phase 3 proposal. Once added to the specification, it is the second numeric data type of JS and will be the 8th basic data type of JS:

* Boolean
* Null
* Udefined
* Number
* BigInt
* String
* Symbol
* Object

&nbsp;

In this article, we'll take a closer look at BigInt and see how it solves the limitations of using the Number type.

### Question:

&nbsp;

Under this standard, very large integers that cannot be accurately represented are automatically rounded off. Specifically, the Number type in JS can only safely represent an integer between -9007199254740991 (-(2^53-1)) and 9007199254740991 (2^53-1), and any integer value outside this range may be lost. Precision.
```javascript
console.log(9999999999999999);    //  10000000000000000
```
```javascript
//Look the last digit
9007199254740992 === 9007199254740993;    // true
```
```javascript
const minInt = Number.MIN_SAFE_INTEGER;	
console.log(minInt);         // → -9007199254740991	
console.log(minInt - 5);     // → -9007199254740996	
// notice how this outputs the same value as above	
console.log(minInt - 4);     // → -9007199254740996
```
```javascript
console.log(9007199254740995n);    // → 9007199254740995n	
console.log(9007199254740995);     // → 9007199254740996
```
```javascript
BigInt("9007199254740995");    // → 9007199254740995n
```

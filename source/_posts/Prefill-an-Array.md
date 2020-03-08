---
title: Prefill an Array
date: 2020-03-08 18:22:01
tags:
    - codewars
---

 ## Kata
Create the function prefill that returns an array of n elements that all have the same value v. See if you can do this without using a loop.

You have to validate input:

v can be anything (primitive or otherwise)
if v is ommited, fill the array with undefined
if n is 0, return an empty array
if n is anything other than an integer or integer-formatted string (e.g. '123') that is >=0, throw a TypeError
When throwing a TypeError, the message should be n is invalid, where you replace n for the actual value passed to the function.

Code Examples:
```text
    prefill(3,1) --> [1,1,1]

    prefill(2,"abc") --> ['abc','abc']

    prefill("1", 1) --> [1]

    prefill(3, prefill(2,'2d'))
      --> [['2d','2d'],['2d','2d'],['2d','2d']]

    prefill("xyz", 1)
      --> throws TypeError with message "xyz is invalid"d
```

### # My Solutions
```javascript
function prefill(n, v) {
  switch(true) {
    case(n !== false && Number(n) === 0):
      return [];
    case(isNaN(Number(n)) || n<0 || n % 1 !== 0 || typeof n == 'boolean'):
      throw new TypeError(`${n} is invalid`);
    default:
      return new Array(n).fill(v);
  }
}
```


### # thoughts
 - 주로 try-catch 처리만 했지, new Error 설정한 경험이 많이 없었는데, 재밌었다.
 - n % 1 !== 0 로 소수점이하 숫자의 유무를 확인할 수 있다.
 - 간단하지만 안해봐서 생각보다 오래 걸렸다. 
 

## references
- [Error 객체에 관하여](https://www.zerocho.com/category/JavaScript/post/5c1913622e014f001e827a89)


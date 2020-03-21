---
title: +1 Array
date: 2020-03-21 18:19:56
tags:
  - codewars
---

## Kata
Given an array of integers of any length, return an array that has 1 added to the value represented by the array.

the array can't be empty
only non-negative, single digit integers are allowed
Return nil (or your language's equivalent) for invalid inputs.

Examples
For example the array [2, 3, 9] equals 239, adding one would return the array [2, 4, 0].

[4, 3, 2, 5] would return [4, 3, 2, 6]



### # Other Answer 
> bignumber 라이브러리 사용

```javascript
const BigNumber = require('bignumber.js');

const upArray = arr =>
  arr.length === 0 || arr.filter(x => x < 0 || x > 9).length > 0
    ? null
    : (new BigNumber(arr.join('')).plus(1))
        .toPrecision()
        .split('')
        .map(Number);
```

### # thoughts
- js 에서 일정 범위를 넘으면 숫자가 그대로 표현되지 않는다.
- 쉬운 문제였지만 오래걸렸던 것은 이 숫자를 어떻게 풀어내느냐가 관건


## references
- [BigInt](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/BigInt)
- [bignumber.js](https://www.versity.co/node_modules/mysql/node_modules/bignumber.js/doc/API.html)
- [JS에서의 64비트 부동소숫점](https://medium.com/@rnrjsah789/js%EC%97%90%EC%84%9C%EC%9D%98-64%EB%B9%84%ED%8A%B8-%EB%B6%80%EB%8F%99%EC%86%8C%EC%88%AB%EC%A0%90-c95e0cfec2b2)

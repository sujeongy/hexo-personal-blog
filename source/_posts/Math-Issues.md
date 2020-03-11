---
title: Math Issues
date: 2020-03-11 18:09:18
tags:
    - codewars
---

## Kata
Oh no, our Math object was "accidently" reset. Can you re-implement some of those functions? We can assure, that only non-negative numbers are passed as arguments. So you don't have to consider things like undefined, null, NaN, negative numbers, strings and so on.

Here is a list of functions, we need:

Math.round()
Math.ceil()
Math.floor()


### # My Solutions
```javascript
var _int, _float;

function checkPeriod(num) {
  _float = num%1;
  _int = num - _float;
}

Math.round = function(number) {
  checkPeriod(number);
  return _float >= 0.5 ? _int + 1 : _int;
};

Math.ceil = function(number) {
  checkPeriod(number);
  return _float > 0 ? _int + 1 : + _int;
};

Math.floor = function(number) {
  checkPeriod(number);
  return _int;
};
```

### # Others
> parseInt, isInteger 메소드를 적절히 사용

```javascript
Math.floor = number => parseInt(number)
Math.round = number => Math.floor(number + 0.5)
Math.ceil  = number => Number.isInteger(number) ? number : Math.floor( number + 1 )
```


### # thoughts
- 간단한 건 직접 구현해보 것도 좋은 공부
- MDN 폴리필도 꼭 한번씩 확인읽어 보는 습관 갖기 


## references
- [Number.parseInt()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Number/parseInt)


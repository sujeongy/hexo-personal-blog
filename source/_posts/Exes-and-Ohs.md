---
title: Exes and Ohs
date: 2020-02-26 10:19:58
tags:
    - codewars
---

## Kata
Check to see if a string has the same amount of 'x's and 'o's. The method must return a boolean and be case insensitive. The string can contain any char.

Example:
```text
XO("ooxx") => true
XO("xooxx") => false
XO("ooxXm") => true
XO("zpzpzpp") => true // when no 'x' and 'o' is present should return true
XO("zzoo") => false
```


### # My Solutions
```javascript
function XO(str) {
  let oCount = xCount = 0;
  let tempStrArr = Array.prototype.slice.apply(str);
  
  tempStrArr.forEach((str) => {
    str = str.toLowerCase();
    if(str === 'o') return oCount++;
    if(str === 'x') return xCount++;
  })
  
  return oCount === xCount;
}
```

### # Others
> 정규식으로 풀이

```javascript
function XO(str) {
  let x = str.match(/x/gi);
  let o = str.match(/o/gi);
  return (x && x.length) === (o && o.length);
}
```

> split() 사용

```javascript
function XO(str) {
    return str.toLowerCase().split('x').length === str.toLowerCase().split('o').length;
}
```

### # thoughts
- split() 사용한 풀이는 굉장히 새로웠다.
> split의 반환값(return)은 배열.
> 
> 위의 풀이는 x, o 를 각각 제외한 배열의 길이로 구현


## references
- [MDN - String.prototype.split()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/split)
- [정규식(Regular Expressions)](https://beomy.tistory.com/21)


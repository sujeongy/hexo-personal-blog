---
title: Array.diff
date: 2020-02-19 23:18:00
tags:
    - 알고리즘
---

## 문자 나열하기 
> 대소문자 관계없이 a-z 알파벳 순서대로 나열값 구하기

```
    [ 'D', 'a', 'G', 'C', 'b', 'e', 'f' ] =>  return [ 'a', 'b', 'C', 'D', 'e', 'f', 'G' ]
```

### # My Solutions
```javascript
// function strSort(arr) {
//  return arr.sort(arr); //Array ["C", "D", "G", "a", "b", "e", "f"]
// }

function strSort(arr) {
  let result = [];
    let mappedObj = arr.map((el, i) => {
      return { idx: i , val: el };
    });

   return result;
}
```

## 문제2 
> 이상정인 잔돈 만들기(10, 50, 100, 500원 사용)

```
    3720원 => 500*7+100*2+10*2
    return { 500: 7, 100: 2, 50: 0, 10: 2};
```

### # My Solutions
```javascript
function arrayDiff(a, b) {
  return a.filter(aItem => !b.includes(aItem));
}
```


## # thoughts
- 어렵지 않았으나 변수명을 어떻게 지을지가 막혔다.

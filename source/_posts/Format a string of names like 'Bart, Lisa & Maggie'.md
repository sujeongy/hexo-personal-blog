---
title: Format a string of names like 'Bart, Lisa & Maggie'
date: 2020-02-19 22:17:49
tags:
    - codewars
---

## Kata
Given: an array containing hashes of names

Return: a string formatted as a list of names separated by commas except for the last two names, which should be separated by an ampersand.

Example:
```javascript
list([ {name: 'Bart'}, {name: 'Lisa'}, {name: 'Maggie'} ])
// returns 'Bart, Lisa & Maggie'

list([ {name: 'Bart'}, {name: 'Lisa'} ])
// returns 'Bart & Lisa'

list([ {name: 'Bart'} ])
// returns 'Bart'

list([])
// returns ''
```
Note: all the hashes are pre-validated and will only contain A-Z, a-z, '-' and '.'.


### # My Solutions
```javascript
function deleteNth(arr,n){
  let result = [];
  let newArr = arr.map(item => {
    let num = 0;
    result.forEach(str => {
      if (item === str) {
        num++;
      }
    })
    if(num === n) return;
    result.push(item);
  });
  return result;
}
```

### # Others
> 메모이제이션

```javascript
function deleteNth(arr,x) {
  var cache = {};
  return arr.filter(function(n) {
    cache[n] = (cache[n]||0) + 1;
    return cache[n] <= x;
  });
}
```

### # thoughts
- 메모이제이션으로 풀면 되겠거니 했는데, 오랜만이라 제시간내엔 구현하지 못했다.
- 현재 내가 구현한 코드는 효용성 최악이다. 각 배열의 요소마다 해당 요소를 계산해주고 있다.
그러므로, 객체를 만들어 각 {'아이템이름':'갯수', .., ..} 구현하는 게 좋다. Best Practices 에서 이미 잘 보여주고 있다.

## references
- [메모이제이션(Memoization) 패턴](https://kool-jay.tistory.com/19)

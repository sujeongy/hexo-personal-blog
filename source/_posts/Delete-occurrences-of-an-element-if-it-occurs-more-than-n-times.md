---
title: Delete occurrences of an element if it occurs more than n times
date: 2020-02-19 21:22:56
tags:
    - codewars
---

## Kata
Enough is enough!
Alice and Bob were on a holiday. Both of them took many pictures of the places they've been, and now they want to show Charlie their entire collection. However, Charlie doesn't like this sessions, since the motive usually repeats. He isn't fond of seeing the Eiffel tower 40 times. He tells them that he will only sit during the session if they show the same motive at most N times. Luckily, Alice and Bob are able to encode the motive as a number. Can you help them to remove numbers such that their list contains each number only up to N times, without changing the order?

Task
Given a list lst and a number N, create a new list that contains each number of lst at most N times without reordering. For example if N = 2, and the input is [1,2,3,1,2,1,2,3], you take [1,2,3,1,2], drop the next [1,2] since this would lead to 1 and 2 being in the result 3 times, and then take 3, which leads to [1,2,3,1,2,3].

Example
```javascript
  deleteNth ([1,1,1,1],2) // return [1,1]

  deleteNth ([20,37,20,21],1) // return [20,37,21]
```


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
- 현재 내가 구현한 코드는 효용성 최악이다. 각 배열의 요소마다 해당 요소를 계산해주고 있다.
- 메모이제이션으로 풀면 되겠거니 했는데, 오랜만이라 제시간내엔 구현하지 못했다.
- 객체를 만들어 각 {'아이템이름':'갯수', .., ..} 구현하는 게 좋다. Best Practices 에서 이미 잘 보여주고 있다.

## references
- [메모이제이션(Memoization) 패턴](https://kool-jay.tistory.com/19)

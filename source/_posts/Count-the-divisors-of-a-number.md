---
title: Count the divisors of a number
date: 2020-02-24 17:05:30
tags:
    - codewars
---

## Kata
Count the number of divisors of a positive integer n.

Random tests go up to n = 500000.

Examples
```javascript
    divisors(4)  = 3  // 1, 2, 4
    divisors(5)  = 2  // 1, 5
    divisors(12) = 6  // 1, 2, 3, 4, 6, 12
    divisors(30) = 8  // 1, 2, 3, 5, 6, 10, 15, 30
```


### # My Solutions
```javascript
function getDivisorsCnt(n){
  let arr = [];
  for(let i=1;i<500000;i++) {
    let val;
    if(n === 1) return n;
    if(arr.includes(i)) return arr.length;
    
    if(!(n%i)) {
      val = n/i;
      arr.push(i);
      if(i !== val) arr.push(val);
    }
  }
}
```

### # Others
> for문

```javascript
function getDivisorsCnt(n) {
  for (var d = 0, i = n; i > 0; i--) {
    if (n % i == 0) d++;
  }
  return d;
}
```

### # thoughts
- 원하는 값은 갯수. 굳이 배열의 길이로 구현하지 않아도 된다.
- !n%i 로 계산하면 제대로 된 연산이 되지 않는다. !(n%i) 감싸줄 것. 

## references
- [산술연산자](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/Arithmetic_Operators)

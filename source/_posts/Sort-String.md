---
title: Sorting arrays of String
date: 2020-02-22 22:19:15
tags:
    - algorithm
---

## 문자배열 재정렬하기 
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

    mappedObj.sort((a, b) => {
      let newA = a.val.toLowerCase(),
          newB = b.val.toLowerCase();
      if(newA > newB) return 1;   
      if(newA < newB) return -1;   
      if(newA === newB) return 0;   
    });

   result= mappedObj.map(item => {
      return item.val;
    });
  
   return result;
}
```

### # Examples
```javascript
var items = [
  { name: 'Edward', value: 21 },
  { name: 'Sharpe', value: 37 },
  { name: 'And', value: 45 },
  { name: 'The', value: -12 },
  { name: 'Magnetic', value: 13 },
  { name: 'Zeros', value: 37 }
];

// value 기준으로 정렬
items.sort(function (a, b) {
  if (a.value > b.value) {
    return 1;
  }
  if (a.value < b.value) {
    return -1;
  }
  // a must be equal to b
  return 0;
});

// name 기준으로 정렬
items.sort(function(a, b) {
  var nameA = a.name.toUpperCase(); // ignore upper and lowercase
  var nameB = b.name.toUpperCase(); // ignore upper and lowercase
  if (nameA < nameB) {
    return -1;
  }
  if (nameA > nameB) {
    return 1;
  }

  // 이름이 같을 경우
  return 0;
});
```

## # reference
- [MDN - Array.prototype.sort()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/sort)

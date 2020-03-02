---
title: Sort the odd
date: 2020-03-02 17:55:35
tags:
    - codewars
---

## Kata
You have an array of numbers.
Your task is to sort ascending odd numbers but even numbers must be on their places.

Zero isn't an odd number and you don't need to move it. If you have an empty array, you need to return it.

Examples:
```javascript
    sortArray([5, 3, 2, 8, 1, 4]) == [1, 3, 2, 8, 5, 4]
```

### # My Solutions
```javascript
function sortArray(array) {
  let oddArr = [], evenObj = [], result = [];
  array.forEach((x, idx) => {
    (x%2)? oddArr.push(x) : evenObj.push({'idx': idx, 'val': x})
  });
  oddArr.sort((a, b) => a - b);
  for(let i=0;i<array.length;i++){
    if(evenObj[0] && evenObj[0]['idx'] === i) {
      result.push(evenObj[0]['val']);
      evenObj.shift();
    } else {
      result.push(oddArr.shift());
    }
  }
  return result;
}
```

### # Others
> Best Practices

```javascript
function sortArray(array) {
  const odd = array.filter((x) => x % 2).sort((a,b) => a - b);
  return array.map((x) => x % 2 ? odd.shift() : x);
}
```

```javascript
function sortArray(array) {
  var odds = [];
  //loop, if it's odd, push to odds array
  for (var i = 0; i < array.length; ++i) {
    if (array[i]%2 !== 0) {
      odds.push(array[i]);
    }
  }
  //sort odds from smallest to largest
  odds.sort(function(a,b){
    return a-b;
  });
  
  //loop through array, replace any odd values with sorted odd values
  for (var j = 0; j < array.length; ++j) {
    if (array[j]%2 !== 0) {
      array[j] = odds.shift();
    }
  }
  
 return array;
}
```


### # thoughts
 - 짝수값을 [] { index: idx, val: value }, .. ] 객체 배열로 만들 필요가 없었다.
 - 배열로만으로 구현 가능
 - odd 배열을 뽑아+정렬한 샅애에서 map을 돌리는 첫번재 풀이.. 멋지다.
 - shift() 보다 pop() 이 성능상 더 빠르다고 한다. sort 시, b - a 으로 변경하는게 좋을듯

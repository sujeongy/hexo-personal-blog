---
title: Array.diff
date: 2020-02-19 23:18:00
tags:
    - codewars
---

## Kata
Your goal in this kata is to implement a difference function, which subtracts one list from another and returns the result.

It should remove all values from list a, which are present in list b.
```javascript
    arrayDiff([1, 2], [1]) == [2]
```

If a value is present in b, of its occurrences must be removed from the other:
```javascript
  arrayDiff([1,2,2,2,3].[2]) == [1,3]
```


### # My Solutions
```javascript
function arrayDiff(a, b) {
  return a.filter(aItem => !b.includes(aItem));
}
```


### # Others
```javascript
function array_diff(a, b) {
  return a.filter(function(x) { return b.indexOf(x) == -1; });
}
```

### # thoughts
- 어렵지 않았으나 변수명을 어떻게 지을지가 막혔다.

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
function list(names){
  let tempNames = names; //arr
  let nameArr = tempNames.map(x => x.name);
  let result;
  
  tempName = nameArr.join(', ');
  let lastName = nameArr[nameArr.length-1];
  result = tempName.replace(`, ${lastName}`, ` & ${lastName}`);
  
  return result;
}
```

### # Others
> 마지막 요소만 따로 떼어 ' & ' 붙이기 

```javascript
function list(names) {
  var xs = names.map(p => p.name)
  var x = xs.pop()
  return xs.length ? xs.join(", ") + " & " + x : x || ""
}
```

> 정규식

```javascript
var list = (names) =>  names.map(x => x.name).join(', ').replace(/(.*),(.*)$/, "$1 &$2")
```

### # thoughts
- 여전히 정규식은 어렵게 다가온다.

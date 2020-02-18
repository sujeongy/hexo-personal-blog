---
title: Disemvowel Trolls
date: 
tags:
    - codewars
---

## Kata
Trolls are attacking your comment section!

A common way to deal with this situation is to remove all of the vowels from the trolls' comments, neutralizing the threat.

Your task is to write a function that takes a string and return a new string with all vowels removed.

For example, the string "This website is for losers LOL!" would become "Ths wbst s fr lsrs LL!".

Note: for this kata y isn't considered a vowel.


### # My Solutions
```javascript
function disemvowel(str) {
//   let tempStr = str;
//   const vowels = ['a', 'e', 'i', 'o', 'u', 'A', 'E', 'I', 'O', 'U'];
  
//   // #1
//   for(let i=0;i<tempStr.length;i++) {
//     if(vowels.includes(tempStr[i])) {
//       str = str.replace(tempStr[i], '');
//     }
//   }
  
  // #2
  str = str.replace(/a|e|i|o|u/gi, '');
  
  return str;
}
```

### # Others
> 정규식으로 풀이

```javascript
function disemvowel(str) {
  return str.replace(/[aeiou]/gi, '');
}
```
[xyz] 문자셋(Character set) 매칭되는 것
[^xyz] 음의 문자셋(negate) or 보수 문자셋(complemented) []안에 있지 않은 문자열과 매칭
ig 대소문자 둘다


### # thoughts
- 우연하게 [어제](https://krystaly.github.io/2020/02/17/Extract-the-domain-name-from-a-URL/)랑 비슷한 유형이라서 바로 정규식으로 풀어봤다.   
- String 문제는 정규식으로 푸는게 좋을거 같다.(아직은 정규식 초보)
- replace, split, slice 모두 새로운 값 반환(+반환값들의 형식도 다시 확인)

## references
- [MDN - String.prototype.replace()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String/replace)
- [MDN - String.prototype.slice()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/slice)
- [MDN - String.prototype.split()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/split)
- [정규식(Regular Expressions)](https://beomy.tistory.com/21)

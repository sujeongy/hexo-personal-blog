---
title: Dubstep
date: 2020-02-29 21:30:23
tags:
    - codewars
---

## Kata
Polycarpus works as a DJ in the best Berland nightclub, and he often uses dubstep music in his performance. Recently, he has decided to take a couple of old songs and make dubstep remixes from them.

Let's assume that a song consists of some number of words (that don't contain WUB). To make the dubstep remix of this song, Polycarpus inserts a certain number of words "WUB" before the first word of the song (the number may be zero), after the last word (the number may be zero), and between words (at least one between any pair of neighbouring words), and then the boy glues together all the words, including "WUB", in one string and plays the song at the club.

For example, a song with words "I AM X" can transform into a dubstep remix as "WUBWUBIWUBAMWUBWUBX" and cannot transform into "WUBWUBIAMWUBX".

Recently, Jonny has heard Polycarpus's new dubstep track, but since he isn't into modern music, he decided to find out what was the initial song that Polycarpus remixed. Help Jonny restore the original song.

Input
The input consists of a single non-empty string, consisting only of uppercase English letters, the string's length doesn't exceed 200 characters

Output
Return the words of the initial song that Polycarpus used to make a dubsteb remix. Separate the words with a space.

Example:
```text
  songDecoder("WUBWEWUBAREWUBWUBTHEWUBCHAMPIONSWUBMYWUBFRIENDWUB")
    // =>  WE ARE THE CHAMPIONS MY FRIEND
```


### # My Solutions
```javascript
function songDecoder(song){
  let result; // str
  let arr = song.split('WUB');//Array ["", "WE", "ARE", "", "THE", "CHAMPIONS", "MY", "FRIEND", ""]
  let newArr = arr.filter(str => {
    return str.length
  });
  result = newArr.join(' ');
  return result;
}
```

### # Others
> 정규식으로 풀이

```javascript
function songDecoder(song){
  return song.replace(/(WUB)+/g," ").trim()
}
```

> split() 사용

```javascript
var songDecoder = (song) => song.split('WUB').filter(x => x !== '').join(' ')
```

```javascript
function songDecoder(song){
  return song.split('WUB').filter((w) => w).join(' ');
}
```
- filter()는 true인 값만 포함해 새배열을 반환해준다.
- Boolean(''), !!'' 은 false
- typeof '' 은 String


### # thoughts
- 문자열(String)은 split() / 배열은 splice()
- split()문자 그대로 배열에 / splice('') 각 char 배열


## references
- [MDN - String.prototype.split()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/split)
- [MDN - Array.prototype.splice()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/splice)



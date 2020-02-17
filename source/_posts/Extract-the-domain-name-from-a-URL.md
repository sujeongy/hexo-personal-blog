---
title: Extract the domain name from a URL
date: 2020-02-17 11:25:47
tags:
    - codewars
---

## Kata
Write a function that when given a URL as a string, parses out just the domain name and returns it as a string. For example:
```javascript
domainName("http://github.com/carbonfive/raygun") == "github" 
domainName("http://www.zombie-bites.com") == "zombie-bites"
domainName("https://www.cnet.com") == "cnet"
```

### # My Solutions
```javascript
function domainName(url){
  const s1 = 'https://',
        s2 = 'http://',
        s3 = 'www.';
  let newUrl = url;
 
  if(url.indexOf(s1)>-1) {
    newUrl = newUrl.slice(s1.length);
  } else if(url.indexOf(s2)>-1) {
    newUrl = newUrl.slice(s2.length);
  }
  if(url.indexOf(s3)>-1) {
    newUrl = newUrl.slice(s3.length);
  }
  
  return newUrl.substring(0, newUrl.indexOf('.'))
}
```

### # Others
> 정규식으로 풀이

```javascript
function domainName(url){
  return url.match(/(?:http(?:s)?:\/\/)?(?:w{3}\.)?([^\.]+)/i)[1];
}
```

> replace() 메소드 사용

```javascript
function domainName(url){
  url = url.replace("https://", '');
  url = url.replace("http://", '');
  url = url.replace("www.", '');
  return url.split('.')[0];
};
```


### # thoughts
 - '정규식으로 풀면 되겠구나!' -> 시간을 재고 푸는중이라 자주 쓰는 방법으로 풀어버렸다.
 - 결국 습관적으로 나오는 코드가 본인 실력이겠거니..
 - 메소드 반환값이 새로운 것을 반환하는지, 기존 것을 수정하는지 확인하자.
 

## references
- [MDN - String.prototype.replace()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String/replace)
- [정규식(Regular Expressions)](https://beomy.tistory.com/21)

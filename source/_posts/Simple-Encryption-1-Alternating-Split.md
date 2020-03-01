---
title: 'Simple Encryption #1 - Alternating Split'
date: 2020-03-01 19:04:41
tags:
    - codewars
---

## Kata
For building the encrypted string:
Take every 2nd char from the string, then the other chars, that are not every 2nd char, and concat them as new String.
Do this n times!

Examples:
```text
    "This is a test!", 1 -> "hsi  etTi sats!"
    "This is a test!", 2 -> "hsi  etTi sats!" -> "s eT ashi tist!"
```

Write two methods:
```javascript
    function encrypt(text, n);
    function decrypt(encryptedText, n);
```
For both methods:
If the input-string is null or empty return exactly this value!
If n is <= 0 then return the input text.


### # My Solutions
```javascript
function encrypt(text, n) {
  if(n<=0) return text;
  if(text==null) return null;
  
  let result;
  let arrEven = [], arrOdd = [];
  let textArr = text.split('');
  
  for(let i=0;i<n;i++){
    for(let r=0;r<textArr.length;r++) {
      (r%2)?arrOdd.push(textArr[r]):arrEven.push(textArr[r]);
    }
    textArr = arrOdd.join('')+arrEven.join('');
    arrOdd = [];
    arrEven = [];
  }
  result = textArr;
  return result;
}

function decrypt(encryptedText, n) {
if(n<=0) return encryptedText;
if(!encryptedText.length) return '';
  
  for(let r=0;r<n;r++) {
    let len = encryptedText.length;
    let divider = (len%2)? (len/2)+1 : len/2;
    let arrEven = encryptedText.slice(-divider || 0).split(''), arrOdd = encryptedText.slice(0, divider || 0).split('');
    encryptedText = [];
    for(let i=0;i<len;i++){
      let val = (i%2)? arrOdd.shift() : arrEven.shift();
      encryptedText.push(val);
  //     result.push(val);
    }
    encryptedText = encryptedText.join('');
  }
  return encryptedText;
}
```

### # Others
> 정규식으로 풀이

```javascript
function encrypt(text, n) {
  for (let i = 0; i < n; i++) {
    text = text && text.replace(/.(.|$)/g, '$1') + text.replace(/(.)./g, '$1') 
  }
  return text
}

function decrypt(text, n) {
  let l = text && text.length / 2 | 0
  for (let i = 0; i < n; i++) {
    text = text.slice(l).replace(/./g, (_, i) => _ + (i < l ? text[i] : ''))
  }
  return text
}
```

> reduce() 메소드 사용

```javascript
function encrypt(text, n=0) {
  return n<1 || text==null ? text : encrypt( [...text].reduce(([a,b],v,i)=> i%2 ? [a+v,b]:[a,b+v],['','']).join(''), n-1)
}

function decrypt(text, n) {
  return n<1 || text==null ? text : decrypt( [...text].slice(text.length/2).map((v,i) => v+text[i] ).join('').slice(0,text.length), n-1)
}
```


> replace() 메소드 사용

```javascript
function encrypt(text, n) {
  if (!text || !text.length || n <= 0)
  {
    return text;
  }

  var res = "";
  var oth = "";

  for (var i = 0; i < text.length; ++i)
  {
    if (i % 2 == 0)
    {
      oth += text[i];
    }
    else
    {
      res += text[i];
    }
  }

  return encrypt(res + oth, --n);
}

function decrypt(encryptedText, n) {
  if (!encryptedText || !encryptedText.length || n <= 0)
  {
    return encryptedText;
  }

  var first = encryptedText.slice(0, encryptedText.length / 2);
  var second = encryptedText.slice(encryptedText.length / 2);
  
  var res = "";
  var i = 0;
  var j = 0;

  while (res.length < encryptedText.length)
  {
    if (res.length % 2 == 0)
    {
      res += second[i];
      i++;
    }
    else
    {
      res += first[j];
      j++;
    }
  }

  return decrypt(res, --n);
}
```


### # thoughts
 - 문제 이해하는데 시간 소모가 컸다.
 - reduce() 풀이는 복기 필요 


## references
- [정규식(Regular Expressions)](https://beomy.tistory.com/21)
- [MDN - String.prototype.replace()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String/replace)
- [MDN - Array.prototype.reduce()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/Reduce)


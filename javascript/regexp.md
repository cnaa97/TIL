# 정규표현식 \(RegExp\)

#### 마지막 \`/\` 뒤 문자열 가져오기

```javascript
var str = 'naver.com/id'
str.match(/\/([^\/]+)\/?$/)[1]; // id
```

#### 숫자만 가져오기

```javascript
var numberPattern = /\d+/g;
'something102asdfkj1948948'.match(numberPattern);
```




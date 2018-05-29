# 정규표현식 \(RegExp\)

#### 마지막 \`/\` 뒤 문자열 가져오기

```javascript
var str = 'naver.com/id'
str.match(/\/([^\/]+)\/?$/)[1]; // id
```




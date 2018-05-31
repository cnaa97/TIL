# 날짜 \(Date\)

#### 'YYYYMMDD' 형식으로 날짜 가져오기

```javascript
Date.prototype.yyyymmdd = function() {
  var mm = this.getMonth() + 1;
  var dd = this.getDate();

  return [this.getFullYear(),
    (mm>9 ? '' : '0') + mm,
    (dd>9 ? '' : '0') + dd
  ].join('');
};

var date = new Date();
date.yyyymmdd();
```




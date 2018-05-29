# 땅따먹기

배열에서 가장 큰 수만 골라 지나오는데, 가장 큰 데이터가 이전 데이터와 같은 인덱스에 있으면 피하고, 얻을 수 있는 가장 큰 수를 리턴한다.

```javascript
function solution(land) {
    var temp;
    var tlen = land.length;
    var slen = land[0].length;
    for(var i = 1; i < tlen; i++) {
        for(var j = 0; j < slen; j++) {
            temp = land[i-1].slice();
            temp[j] = 0;
            land[i][j] += Math.max.apply(null, temp);
        }
    }
    return Math.max.apply(null, land[land.length-1]);
}

solution([[1,2,3,5], [5,6,7,8], [4,3,2,1]]); // 16
```

위 문제는 동적 프로그래밍\(DP\)을 이용하면 해결할 수 있다. 매개변수로 전달받은 land 데이터를 수정하면서 가장 큰 수를 찾아 업데이트한다. 그리고 가장 마지막에 남는 2차원 배열의 마지막 인덱스에 있는 값을 리턴한다.


# 순차 탐색 \(linear search\)

```javascript
function linearSearch(arr, target){
  for (let i=0; i<arr.length; i++) {
    if (arr[i] === target) {
      return i;
    }
  }
  return -1;
}
```

### 성능 분석

* 순차 탐색은 하나의 루프가 필요하다.
* 삽입 알고리즘의 시간복잡도는 `O(1)`
* 삭제 알고리즘은 `O(n)`


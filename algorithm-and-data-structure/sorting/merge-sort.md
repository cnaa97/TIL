# 합병 정렬 \(Merge sort\)

![](../../.gitbook/assets/image%20%2810%29.png)

* 분할정복 방법
* 복잡도 `O(nlogn)`

```javascript
function mergeSort(arr) {
  // 배열이 하나일 때는 그대로 리턴
  if (arr.length < 2) return arr;

  const middle = Math.floor(arr.length / 2); // 가운데 인덱스
  const left = arr.slice(0, middle); // 좌측 배열
  const right = arr.slice(middle, arr.length); // 우측 배열

  return merge(mergeSort(left), mergeSort(right));
}


function merge(left, right) {
  const result = [];

  while (left.length && right.length) {
  if (left[0] <= right[0]) {
    result.push(left.shift()); // 더 작은 수를 삽입
  } else {
    result.push(right.shift());
  }
}

  while (left.length) {
    result.push(left.shift());
  }

  while (right.length) {
    result.push(right.shift());
  }

  return result;
}

mergeSort([20, 15, 35, 50, 40, 10, 30, 25])
// [ 10, 15, 20, 25, 30, 35, 40, 50 ]
```


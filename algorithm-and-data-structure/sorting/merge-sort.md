# 합병 정렬 \(Merge Sort\)

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

![](../../.gitbook/assets/image%20%284%29.png)

![](https://camo.githubusercontent.com/64ba2bcbd5c11779657e40a1d03d0ea691f6fa57/68747470733a2f2f75706c6f61642e77696b696d656469612e6f72672f77696b6970656469612f636f6d6d6f6e732f632f63632f4d657267652d736f72742d6578616d706c652d33303070782e676966)




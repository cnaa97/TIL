# 선택 정렬 \(Selection Sort\)

* 주어진 데이터 중 가장 작은 값부터 차례대로 **선택**해서 나열하는 방식
* 정렬되지 않은 데이터 중 가장 작은 값 선택 후 첫 번째 요소와 교환
* 시간복잡도 O\(n²\)

```javascript
function selectionSort(array) {
  const len = array.length;
  let minIndex, temp;
  
  for (i = 0; i < len - 1; i++) { // 처음부터 훑으면서
    minIndex = i;
    for (j = i + 1; j < len; j++) { // 최솟값 위치 찾고
      if (array[j] < array[minIndex]) {
        minIndex = j;
      }
    }
    temp = array[minIndex]; // 최솟값 저장
    array[minIndex] = array[i];
    array[i] = temp; // 최솟값을 앞으로 전달
  }
  return array;
};

selectionSort([5,1,4,7,2,6,8,3]); // [1,2,3,4,5,6,7,8]
```



![](../../.gitbook/assets/image%20%285%29.png)

![](../../.gitbook/assets/image%20%281%29.png)


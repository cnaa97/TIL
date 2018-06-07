# 이진 탐색 \(Banary search\)

* 이진탐색은 정렬된 상태로 문제가 주어졌을 때 효과적으로 수행된다.
* 분할정복 방법으로 수행되는  알고리즘 중 대표적인데, 하향식 접근 방법이다. 

![](../../.gitbook/assets/image%20%2810%29.png)

#### 반복문으로 구현

```javascript
function binarySearch(arr, target){
 let min = 0;
 let max = arr.length - 1;
 let guess;
 
 while(min <= max) {
   // min, max의 가운데 값 초기화
   guess = Math.floor((min + max) / 2);
   
   if (arr[guess] === target) {
     return guess;
   } else if (arr[guess] < target) {
     min = guess + 1;
   } else {
     max = guess - 1;
   }
 }

  return -1;    
}

binarySearch([2, 3, 5, 7, 11, 13, 17, 19], 5); // 2
```

#### 성능 분석

* `O(logn)`
* 정렬되어있지 않다면, 정렬 `O(nlogn)` 의 시간이 필요




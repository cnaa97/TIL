---
description: 정수 배열에서 이어지는 가장 큰 원소의 합 구하기
---

# 가장 큰 원소의 합 구하기

처음에는 문제 자체를 이해못했는데, 배열의 첫 번째 값부터 시작해서, 가장 큰 다음 수를 찾아 합치는 문제이다. DP를 사용하면 해결할 수 있다.

```javascript
function solution(arr){
  // DP 구현을 위해 max, sum 이라는 변수를 선언한다
  let max = arr[0];
  let sum = arr[0];

  for (let i=1; i<arr.length; i++){
    // 먼저 현재 합과 배열의 각 원소를 더한 합을 비교하고 더 큰 값을 선택한다
    sum = Math.max(arr[i]+sum, arr[i]);
    // 합과 최대값 중 더 큰 값을 선택한다
    max = Math.max(sum, max);
  }
  // 루프를 마치면 max에 가장 큰 값이 들어있
  return max;
}

solution([-1, 3, -1, 5]) // 7 (3 + (-1) + 5)
```


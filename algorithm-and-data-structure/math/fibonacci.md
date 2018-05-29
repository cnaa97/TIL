# 피보나치 수 \(Fibonacci\)

피보나치 수는 F\(0\) = 0, F\(1\) = 1일 때, 1 이상의 n에 대하여 F\(n\) = F\(n-1\) + F\(n-2\) 가 적용되는 점화식이다.

```text
0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89, 144, ...
```

```javascript
function fibonacci(num) {
  if (num <= 1) {
    return num;
  } else {
    return fibonacci(num - 1) + fibonacci(num - 2);
  }
}
```

재귀 함수를 사용해야 시간복잡도에서 좋은 결과가 나온다.


# factorial \(계승\)

```text
5! = 5 * 4 * 3 * 2 * 1 = 120
```

#### 첫 번째 방법

```javascript
function factorial(num){
  if (num === 0 || num === 1){
    return 1;
  } else {
    return num * factorial(num-1);
  }
}

factorial(5); // 120
```

#### 두 번째 방법

```javascript
function factorial(number) {
  let result = 1;

  for (let i = 1; i <= number; i += 1) {
    result *= i;
  }

  return result;
}
```


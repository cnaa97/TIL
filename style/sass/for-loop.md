---
description: for loop that increments by a value
---

# for loop

```css
@for $i from 1 through 50 {
  $value: $i * 2 - 1;
  // stuff
}
```

```css
.bi-rotate-{
  @for $i from 1 through 6 {
    $value: $i * 45;
    &#{$value}{
      -webkit-transform: rotate($value + 0deg);
      -moz-transform: rotate($value + 0deg);
      -ms-transform: rotate($value + 0deg);
      -o-transform: rotate($value + 0deg);
      transform: rotate($value + 0deg);
    }
  }
}
```

컴파일 시 `.bi-rotate-45, .bi-rotate-90 ... .bi-rotate-270` 까지 CSS 클래스가 생성된다.

```css
.bi-rotate-45 {
  -webkit-transform: rotate(45deg);
  -moz-transform: rotate(45deg);
  -ms-transform: rotate(45deg);
  -o-transform: rotate(45deg);
  transform: rotate(45deg);
}
```


---
description: 'CSS에서 특정 엘리먼트(ex: 이미지)의 가로, 세로 비율을 유지하는 방법'
---

# Aspect Ratio

```markup
<div class="container--fixed-width">
  <figure class="image--fixed-ratio">
    <img src="http://placehold.it/300x400">
  </figure>
</div>
```

```css
.container--fixed-width {
  width: 60%;
}

.image--fixed-ratio {
  width: 100%;
  padding-top: 100%; /* padding-top의 값을 이용해 비율을 조정한다. */
  position: relative;
}

img {
  width: 100%;
  height: 100%;
  position: absolute;
  top: 0;
  left: 0;
}
```




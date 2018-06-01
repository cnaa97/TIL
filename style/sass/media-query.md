# Media Query

### 변수 사용

```css
$break-small: 320px;
$break-large: 1200px;

.profile-pic {
  float: left;
  width: 250px;
  @media screen and (max-width: $break-small) {
    width: 100px;
    float: none;
  }
  @media screen and (min-width: $break-large) {
    float: right;
  }
}
```

### 전체 쿼리를 포함한 변수 사용

```css
$information-phone: "only screen and (max-width : 320px)";

@media #{$information-phone} {
  background: red;
}
```

### 콜론 사용

```css
$width-name: max-device-width;
$target-width: 320px;

@media screen and ($width-name : $target-width) {
  background: red;
}
```

### 조건을 미리 정의해두고 사용

```css
$break-small: 320px;
$break-large: 1024px;

@mixin respond-to($media) {
  @if $media == handhelds {
    @media only screen and (max-width: $break-small) { @content; }
  }
  @else if $media == medium-screens {
    @media only screen and (min-width: $break-small + 1) and (max-width: $break-large - 1) { @content; }
  }
  @else if $media == wide-screens {
    @media only screen and (min-width: $break-large) { @content; }
  }
}

.profile-pic {
  float: left;
  width: 250px;
  @include respond-to(handhelds) { width: 100% ;}
  @include respond-to(medium-screens) { width: 125px; }
  @include respond-to(wide-screens) { float: none; }
}
```


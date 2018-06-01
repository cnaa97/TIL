# mixin example

```css
@mixin webfont() {
    font-family: webfont, sans-serif;
    font-weight: 700;
}
.foo {
    @include webfont();
}
```

#### width 동적 설정

```css
@mixin truncate($width: 100%) {
    width: $width;
    max-width: 100%;
    display: block;
    overflow: hidden;
    white-space: nowrap;
    text-overflow: ellipsis;
}

.foo {
    @include truncate(100px);
}
```




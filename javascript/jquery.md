# jQuery 분석

#### jQuery는 어떻게 `$`변수를 사용하도록 만들까?

익명함수를 통해 주입된 전역 스코프 \(`window`\)에서 내부 변수 `jQuery` 함수를 `window.$` 변수에 할당한다.

#### `$(function() { 내용 });` 은 어떻게 기능하나?

 `$( document ).ready()` 와 동일한 기능을 하는 위 코드는 DOM이 모두 로드된 후 한 번 실행된다. jQuery에서는 해당 파라미터의 타입이 함수인지 체크를 해서 `ready`가 실행되도록 한다.

#### $\(선택자\)는 어떻게 작동하나?

선택자가 문자열인 경우 `jQuery.find` 함수가 실행되는데, jquery의 `find` 함수는 내부 `prototype`에서 다른 함수와 함께 정의되어 있다.

```javascript
jQuery.fn = jQuery.prototype = {
  ...
  find: function(t){}
}
```

#### jQuery 플러그인에서 사용하는 `$.fn`은 무슨 원리인가 

플러그인을 만들 때 사용하는 fn은 jquery의 prototype이다. 플러그인에서는 jQuery 객체의 프로토타입으로 플러그인의 해당 기능을 주입시키는 것이다.

#### jQuery의 메서드 체이닝은 어떻게 작동하나?

jquery의 **디자인 패턴**인데, 함수의 리턴 값을 자신\(`this`\)로 지정했기 때문에 체이닝이 가능하다.


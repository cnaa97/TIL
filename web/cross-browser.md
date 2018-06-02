---
description: 크로스 브라우저 (Cross Browser)
---

# Cross Browser

### 정의

크로스 브라우징이란 HTML, CSS, JS 작성시 W3C의 웹 표준에 맞는 코딩을 함으로써 어느 유저 에이전트에서 사이트가 제대로 보여지고 작동되도록 하는 기법을 말한다.

에이전트의 파편화로, 각 브라우저 마다 동작하지 않는,  스크립트, 마크업 코드가 존재하고, 해석하지 못하는 CSS 코드가 있기 때문에 크로스 브라우징이 필요하다. 



### 대응

1. [Can I Use](http://caniuse.com/) 사용
2. 버그 리포트 참고 Github의 [Flexbox 버그 리포팅 저장소](https://github.com/philipwalton/flexbugs)를 참고한다. 
3. 보수적인 코딩 새로운 기술을 익히되, 기존 기술을 유용하게 활용한다. 예컨대 플랙스박스로 레이아웃을 구현하면 편하지만, 지원하지 않는 브라우저가 있고, 폴리필을 적용하더라도 사이트가 느려진다. 
4. 브라우저 트렌드
5. 브라우저 대응 순서 가장 점유율이 높은 브라우저부터 확인하자.



### 예제

#### IE 호환성 문제 해결

```markup
<meta http-equiv="X-UA-Compatible" content="IE=edge">
```

`IE=edge`는 최신모드로 지정된 `DOCTYPE`에 상관없이 IE8 이상 버전에서 항상 최신 표준 모드로 렌더링됩니다.

#### 기능 탐지

```javascript
function getElement(id) {
  if (document.getElementById) {
    return document.getElementById(id);
  } else if (document.all) {
    return document.all[id];
  } else {
    throw new Error("No way to get element");
  }
}
```

IE5 이전 버전에서는 `document.getElementById` 메서드가 지원되지 않기 때문에, 위와 같은 코드로 기능을 탐지하여 대응한다. 위 코드에서는 비표준인 `document.all` 함수를 사용한다.

#### 브라우저 탐지

```javascript
navigator.userAgent 
```

#### 랜더링 엔진

* 게코
* 웹킷
* 인터넷 익스플로러
* KHTML
* 오페라



### 브라우저 별 대응

#### 데스크톱

* IE
  * 일반적으로 IE8, 특수한 경우 IE7, 최신버전 대응이면 IE9
* 크롬
  * 최신 버전 기준
* 파이어폭스
* 사파리, 오페라, 비발디, 브레이브 등

#### 모바일

* 사파리
  * PC랑 비슷하며, fixed, input 쓸 때 유의 필요.
  * Flex 부분 이슈
* 크롬
  * 최신 버전
* 파이어폭스

#### 웹뷰

* 환경이 없을 때는 네이버 앱에서
* 혹은 리액트 네이티브로 만들어서 사용




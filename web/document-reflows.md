---
description: Document Reflows는 성능 최적화(Performance Optimization)에 영향을 미치는 요소 중 하나이다.
---

# Document Reflows

### Document Reflows

문서 내 요소의 위치, 도형을 다시 계산하기 위한 웹브라우저 프로세스의 이름

### Reflows trigger

* 브라우저 창 크기 변경
* 스타일을 계산하는 자바스크립트 메서드 사용
* DOM 요소 추가, 삭제
* 클래스 변경

### Prevent Layout thrashing

Read - Write 구조가 반복적으로 사용된다면, 최초에 그려진 레이아웃은 **무효화**되고 다시 리플로우 하게 된다.

```javascript
// Read
var h1 = element1.clientHeight;
// Write (invalidates layout)
element1.style.height = (h1 * 2) + 'px';
// Read (triggers layout)
var h2 = element2.clientHeight;
// Write (invalidates layout)
element2.style.height = (h2 * 2) + 'px';
```

아래와 같이 분리해서 작성하면 된다.

```javascript
// Read
var h1 = element1.clientHeight;
var h2 = element2.clientHeight;
// Write
element1.style.height = (h1 * 2) + 'px';
element2.style.height = (h2 * 2) + 'px';
// document reflows at end of frame
```

* width, height와 같은 **레이아웃 속성의 변경**은 특정 요소의 위치와 크기 파악에 오랜 시간이 걸린다.
* CSS **flexbox**를 사용하면 성능에 도움이 된다.


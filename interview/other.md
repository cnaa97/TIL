# Other

### 웹앱/웹사이트 구축 시 고려해야 할 UI, Security, Performance, SEO, Maintainability 에 대해서 설명해주세요.

### 선호하는 개발 환경에 대해 자유롭게 이야기해 주세요.

### 웹 페이지를 만들 때의 과정은?

### 만약 리액트, 앵귤러 등 라이브러리를 사용하지 않고 바닐라JS로 SPA를 만든다고 할 때 어떻게 설계/개발 할 것인지?

### 점진적 향상법\(progressive enhancement\)과 우아한 성능저하법\(graceful degradation\)의 차이는?

점진적 향상법은 오래된 기기 혹은 낮은 버전의 브라우저에 맞추고, 여러 테스트를 통해 기능을 점진적으로 향상시키는 것. 우아한 성능 저하법은 최신 기술에 맞춘 후 오래된 기기 혹은 기술에서도 동작하도록 하기 위해 최적화시키는 방법. 

#### 웹사이트에서 assets/resources를 최적화하는 방법은?

#### 브라우저가 한 번에 1개의 도메인에서 내려받는 자원은 몇 개인가요? 예외에는 어떤 것들이 있나요?

### RESTful 쓰는 이유

* API 메시지만 보고도 이를 쉽게 이해 할 수 있는 자체
* 클라이언트 - 서버 구조
* 상태 정보를 따로관리 하지 않기 때문에 들어오는 요청만 처리

### 페이지 로드 시간을 줄이는 방법은?

* 자바스크립트 압축
* 이미지 등 리소스는 압축
* js 를 불러들이는 순서를 고려해서 동적 로딩 방법 변경 \(window.onload 등\)
* 백엔드에서는 gzip 등을 활용해 데이터 압축

### 프로젝트에 합류했는데, 기존 멤버는 Tab을 이용하고, 당신은 Sapce를 사용했을 때, 어떻게 할 지?

**retab**을 사용하는 방법을 생각하겠지만, 정말 중요한 룰로 작용한다면 코딩 습관을 바꾸는 쪽도 고려할 것.

### 간단한 슬라이드쇼를 만드는 방법은?

* `position: absolute; left: width;` 를 기반으로 모든 페이지를 좌측으로 정렬 시키고, 자바스크립트로 left 값을 변경하는 식. 
* 직접 스타일을 조작하는데 리플로우, 리드로우와 같이 퍼포먼스 문제가 있다면 CSS3 transform을 사용할 것.

### HTTP 1.0, 1.1의 차이는?



### HTTP **`Keep-Alive`**란?

* HTTP는 **connection less** 방식으로 연결을 매번 끊고 새로 연결하는 구조
* 이는 네트워크에서 많은 비용을 소비하는 구조 \(최초 연결하기 위한 준비 과정\) 
* 그래서 HTTP 1.1부터는 **Keep-Alive** 기능 지원
* **Keep Alive**란 연결된 소켓에 IN/OUT의 access가 마지막으로 종료된 시점부터 정의된 시간까지 access가 없더라도 대기하는 구조. 
* 즉 정의된 시간 내에 접근이 이루어진다면 계속 연결된 상태를 유지할 수 있다는 것
* Keep-Alive time out 내에 클라이언트에서 request를 재요청 시, 소켓\(포트\)를 새로 여는 것이 아니라 이미 열려 있는 소켓에 전송하는 구조
* 클라이언트는 http 1.1을 준수하고, `Connection: Keep-Alive`를 서버에 요청
* 서버에서도 http 1.1 스펙을 구현하고 **keep alive** 기능 활성화 후, keep alive time out 설정

### JWT에 대해서. expire 되는 것은 어디에서 체크하는지?

### 만약 올해 기술 책임자가 됬다면 무엇을 먼저 할 건가요?

### 표준의 중요성에 대해 설명해주세요.

### Flash of Unstyled Content란? FOUC를 피하기 위해서는?

* 스타일시트가 로드되기 전에 잠시 스타일이 먹히지 않은 화면이 나타나는 현상.
* 극단적으로는 body의 visibility를 hidden시키고 onload 속성를 적용하여 스크립트 로딩 후 body를 visible시키는 방법

```markup
<body style="visibility: hidden;" onload="js_Load()">
```

```javascript
function js_Load(){ 
  document.body.style.visibility = 'visible';
}
```

### CSS 애니메이션과 JavaScript 애니메이션의 차이는?

* 애니메이션을 세밀하게 표현해야할 경우 자바스크립트
* 간단한 전환은 CSS 애니메이션 사용
* 자바스크립트에서 애니메이션 구현 시 `requestAnimationFrame`메서드를 사용하는 것을 권장
* jQuery의 경우 `setInterval`을 사용하기 때문에 퍼포먼스 문제가 있을 수 있음.

### CORS 란?

Cross-Origin Resource Sharing으로, 도메인과 다른 도메인으로부터 리소스를 요청할 경우 보안 문제로 브라우저에서 막히는 경우가 있는데, 서버단에서 크로스도메인 요청을 허용하거나 jsonp 등의 방법으로 대응할 수도 있다.




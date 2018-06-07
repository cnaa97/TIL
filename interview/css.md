# CSS

#### CSS 선택자의 특이성\(specificity\)과 작동 원리는?

* 브라우저는 CSS 특수성에 따라 요소에 표시할 스타일 결정
* 각 규칙에 따라 특수성, 4개의 쉼표로 구분된 값 `a, b, c, d`  계산
  * `a`는 인라인 스타일의 사용 여부. 인라인이면 1, 아니면 0
  * `b`는 id 셀렉터의 수
  * `c`는 클래스, 속성 및 가상 클래스 선택자의 수
  * `d`는 태그 및 유사 요소 선택자의 수
* 결과값은 점수가 아니라, 비교할 수 있는 가치들의 행렬이다.
* 선택자에서 가장 높은 특이성을 갖는 항목을 결정할 때, 가장 높은 값을 보고 비교한다.

#### "Resetting"과 "Normalizing" CSS 의 차이점 및 어떤 것을 선택할 건가요?

* Resetting
  * 요소의 **모든 기본 브라우저 스타일을 제거**하기 위한 것.
  * 예를 들어 margin, padding,font-size는 같은 값으로 재설정하는 것.
  * 일반적인 타이포그래피 요소에 대한 스타일을 재선언해야한다.
* Normalizing
  * 모든 것을 정리하는 것이 아니라 **유용한 기본 스타일은 보존**. 
  * 일반적인 브라우저 종속성에 대한 버그 수정.
* 주로 reset을 사용하는데, 완전히 새로운 디자인을 해야할 경우 유용.

#### `float`의 작동 원리는?

* 위치 지정 속성
* 페이지 흐름의 일부로 남아 엘리먼트가 **'뜬'** 상태를 표현
* 흐름에서 제거되는 `absolute`와 달리 위치 지정에 영향을 줌.
* 해당 엘리먼트의 높이가 무효화됨.
* 상위 엘리먼트에 `overflow: auto` 혹은 `overflow: hidden` 속성으로 자식을 포함하도록 할 수 있으나, 컨테이너가 닫히기 전 float을 clear 속성으로도 해결할 수 있음.
* clear 속성은 float된 엘리먼트의 높이가 사라짐으로 인해 다음 엘리먼트의 레이아웃이 깨지는 현상을 처리할 수 있음. 
* float 엘리먼트 아래에 위치하여 사용.
* css :after 선택자로 간단히 해결할 수도 있음.

#### `clear`하는 방법

* 비어있는 div 사용

```markup
<div style="clear: both;"></div>
```

* clearfix 사용

```css
.clearfix:after {
  content: ' ';
  visibility: hidden;
  display: block;
  height: 0;
  clear: both;
}
```

* 부모는 overflow를 통해 새로운 BFC를 설정하고, 확장된 자식을 포함한다.

```http
<div style="overflow: auto;">
  <div style="float: left;">Div 1</div>
  <div style="float: left;">Div 2</div>        
</div>
```

자식이 부모보다 크기가 경우 overflow: hidden은 자식의 모두 보여줄 수 없다.

#### `z-index`와 stacking context 형성 원리는?

* CSS 의 `z-index`속성은 겹치는 요소의 순서를 제어한다. 
* `z-index`는 `static`이 아닌 `position` 값을 갖는 요소에만 영향을 준다.
* `z-index` 값이 없으면 DOM에 나타나는 순서대로 요소가 쌓인다. 
  * 동일한 레이어에서 **가장 낮은 레이어의 맨 위**에 나타난다.
* 정적이지 않은\(non-static\) 포지션 지정 요소 \(및 해당 하위 요소\)는 HTML 레이어 구조와 상관없이 기본 정적 위치 지정을 사용하여 항상 요소 위에 나타납니다.
* 쌓임 맥락\(stacking context\)은 레이어 집합을 포함하는 요소
* 자식의 `z-index` 값은 문서 루트가 아닌 해당 요소를 기준으로 설정됨. 
* 부모 A의 `z-index`가 형제 B보다 작은 경우, A의 자식이 B보다 더 크더라도 B보다 더 높이 위치할 수 없음.

#### 블록 서식 문맥\(BFC, Block formatting context\)과 작동 방식

* BFC는 블록 레벨 요소를 랜더링하는 CSS의 비주얼 서식 모델 중 하나이다.
* 이 안에서 블록 박스의 레이아웃이 결정되며, float 끼리 서로 영향을 준다.
* 다음 중 하나에 의해 블록 포맷 컨텍스트가 생성된다.
  * 루트 또는 이를 포함하는 요소
  * floats \(none이 아닌 경우\)
  * absolute, fixed로 배치된 요소
  * inline-block
  * table-cell
  * table-caption
  * overflow visible \(그 값이 viewport 에 전파되었을 때는 제외\)
* 각 박스의 왼쪽 상단은 블록의 왼쪽 상단에 닿는다.

#### CSS 스프라이트\(sprites\)란?

* 여러 이미지를 하나의 큰 이미지로 결합하여 아이콘에 주로 사용됨.
* 여러 이미지를 하나로 묶어 적절한 CSS 생성
* 각 이미지는 `background-image`, `background-position`, `background-size` 속성이 정의된 CSS 클래스를 통해 적용될 수 있음.
* html에서 엘리먼트에 클래스를 추가하는 방식으로 사용.
* 여러 이미지에 대한 HTTP 요청 수를 줄일 수 있음.
  * HTTP2에선 더이상 중요하지 않음.
* hover 상태에서만 나타나는 이미지 필요 시, 이미지가 미리 다운로드 되기 때문에 깜빡이지 않음.

#### 크로스 브라우징에서 스타일 문제를 해결하는 방법

* 문제를 일으키는 브라우저를 식별한 후, 해당 브라우저가 사용 중일 때만 로드되는 별도의 스타일 시트를 사용한다. 하지만 이는 서버 사이드 렌더링이 필요하다.
* 부트스트랩 등의 라이브러리를 사용한다.
* **autoprefixer**를 사용해 자동으로 벤더 프리픽스를 추가한다.
* Reset CSS 또는 Normalize.css 를 사용한다.

#### 기능이 제한된 브라우저의 페이지는 어떻게 처리하며, 어떤 기술/프로세스를 사용하나요?

* 우아한 퇴화 최신 브라우저를 위한 응용 프로그램을 구축하는 동시에 그것이 구형 브라우저에서도 계속 작동하도록 하는 구축 방법.
* 점진적 향상 기본 수준의 사용자 환경에 대한 응용 프로그램을 구축하지만, 브라우저가 이를 지원할 경우 기능을 강화하는 방법.
* [caniuse.com](https://caniuse.com/)을 사용하여 기능 지원 확인.
* Autoprefixer 사용
* [Modernizr](https://modernizr.com/) 사용

#### 특정 콘텐츠를 시각적으로 숨기고, 스크린 리더기에서만 읽히도록 하는 방법은?

접근성\(a11y\)과 관련된 문제

```css
.hide1 {
  visibility: hidden; /* 숨기지만, 공간은 차지함 */
  width: 0;
  height: 0; /* 공간 차지하지 않도록 처리 */
}

.hide2 {
  position: absolute; 
  left: -99999px
}

/* 블록 엘리먼트에서만 작동 */
.hide3 {
  text-indent: -9999px; 
}
```

* [WAI-ARIA](https://www.w3.org/TR/wai-aria-1.1/) 웹 페이지의 액세스 가능성을 높이는 방법을 지정하는 W3C 기술 사양. \(이상적인 해결책\)
* `absolute` 접근법이 가장 간단하며 대부분 요소에서 작동

#### screen 이 아닌 @media 속성의 예

총 4 가지 종류

* **all** - 모든 미디어 기기 장치
* **print** - 프린터
* **speech** - 화면을 소리내어 읽는 스크린 리더
* **screen** - 컴퓨터 스크린, 태블릿, 스마트 폰 등

```css
@media print {
  body {
    color: black;
  }
}
```

#### CSS 선택자에 일치하는 요소가 어떤 것인지 브라우저는 어떻게 결정하나요?

* 브라우저는 오른쪽에서 왼쪽으로 선택자가 일치하는지 확인한다. 
* 브라우저는 선택자에 따라 DOM 요소를 필터링하고 해당 부모 요소를 검사하여 일치하는지 판별한다. 
* 선택자 체인의 길이가 짧을수록 해당 요소가 선택자와 일치하는지 여부를 빠르게 판별할 수 있다. 
* 그러므로 태그 선택자 및 일반적인 선택자를 사용하는 것은 성능에 도움이 되지 않는다.

예를 들어, 선택자 `p span`을 사용할 경우 브라우저는 먼저 모든 &lt;span&gt;요소를 찾아 그 부모의 루트까지 모두 통과하여 `<p>`요소를 찾는다. 특정 `<span>`의 경우 `<p>`를 찾는 즉시 `<span>`이 일치하는 것을 알고 있으며, 이에 따라 매칭을 중지한다.

#### id, class, inline style, !important를 우선순위 순으로 나열한다면?

1. !important
2. inline style
3. id
4. class
5. tag

#### 효율적인 CSS를 작성하는데 있어 어려움은?

* 효율적인 선택자를 구성하는 것. \(퍼포먼스 문제\)
* [BEM \(Block, Emenent, Modifier\)](https://en.bem.info/) 방법론
  * BEM 방법론에서는 모두 단일 클래스를 갖고, 계층 구조는 필요한 곳에서의 확장을 권장한다. 
  * 따라서 쉽고 효율적으로 선택자를 재정의할 수 있다.
* 특정 CSS 속성이 리플로우, 리페인트, 합성을 트리거하는지 알아두면 좋다. 
  * 가능하면 레이아웃\(리플로우 트리거\)을 변경하는 스타일은 작성하지 말라.

[https://developers.google.com/web/fundamentals/performance/rendering/](https://developers.google.com/web/fundamentals/performance/rendering/)

#### CSS 전처리기 사용의 장단점은?

**장점**

* 유지보수 향상
* 중첩 선택자를 작성하기 쉬움
* 일관된 스타일링 설정을 위한 변수 사용. 
  * 테마 파일을 공유 가능.
* 반복되는 CSS 를 위한 Mixins 생성.
* 코드를 여러 파일로 나눌 수 있음. 

**단점**

* 전처리기를 위한 도구 필요
* 다시 컴파일하는 시간이 느릴 수 있음

#### 비표준 글꼴을 사용하는 웹디자인을 구현하는 방법은?

`font-face`에서 커스텀 폰트를 정의하고,  `font-weight`가 다른 경우 `font-family`를 정의한다.

#### Pseudo-elements 란?

* CSS Pseudo-element 는 Selector 에 추가된 키워드
* 선택한 요소의 특정한 부분을 스타일링 할 수 있음
* 마크업을 수정하지 않고 \(`:before`, `:after`\) 데코레이션을 위해 사용하거나 \(`:first-line`, `:first-letter`\) 또는 마크 업에 요소를 추가할 수 있다. \(`content: ''` 와 결합\)
* `:first-line` 과 `:first-letter` 는 텍스트를 데코레이션하는데 사용된다.
* `.clearfix` 에 사용되어 `clear: both` 로 영역을 차지하지 않는 요소를 추가하기도 한다.
* 툴팁의 삼각형 화살표는 `:before` 와 `:after` 사용
  * 삼각형이 실제로 DOM 이 아닌 스타일의 일부로 간주되기 때문에 분리하는 것이 좋다. 
  * 추가적인 HTML 요소를 사용하지 않고 CSS 스타일만으로 삼각형을 그릴 수는 없다.

#### 박스 모델이란? 박스 모델로 레이아웃을 랜더링하는 방법은?

* CSS 박스 모델은 문서 트리의 요소에 대해 생성되고, 시각적 서식 모델에 따라 배치된 사각형 상자를 나타낸다.
* 각 박스에는 content 영역 \(예: 텍스트, 이미지 등\) 및  'padding', 'border' 및 'margin' 영역이 있다.

CSS 박스 모델은 다음을 계산한다.

* 블록 요소가 차지하는 공간.
* 테두리 또는 여백이 겹치거나 붕괴되는지 여부.
* 박스의 크기.

박스 모델에는 다음과 같은 규칙이 있다.

* 블록 요소의 크기는 `width`, `height`, `padding`, `border`, `margin`에 의해 계산된다.
* `height`가 지정되어 있지 않은 경우, \(아래에 float 가 없다면\) 블럭 요소는 포함하고있는 내용 만큼의 높이를 가질 것이고, `padding` 을 덧붙일 것이다 
* `width`가 지정되지 않으면, float 가 아닌 블록 요소는 \(부모의 너비 - `padding`\) 에 맞게 확장됩니다.
* 요소의 `height`는 내용의 `height`에 의해 계산된다.
* 요소의 `width`는 내용의 `width`에 의해 계산된다.
* 기본적으로 `padding`과 `border`는 요소의 `width`와 `height`의 일부가 아니.

#### `* { box-sizing: border-box; }` 의 기능과 장점은?

* 기본적으로, 요소들은 `box-sizing: content-box`가 적용되고, 내용의 크기만 고려된다.
* 해당 요소는 가로, 세로 계산 방법을 변경해 border, padding도 함께 포함시킨다.
* 요소의 세로 크기는 내용의 height + 수직 padding + 수직 border 폭에 의해 계산된다.
* 요소의 가로 크기은 내용의 width + 수평 padding + 수평 border 폭에 의해 계산된다.

**`inline` 과 `inline-block` 의 차이점은?**

|  | `block` | `inline-block` | `inline` |
| --- | --- | --- | --- | --- | --- |
| 크기 | 부모 컨테이너의 너비 채움 | 내용에 따라 달라짐 | 내용에 따라 달라짐 |
| 위 | 새 줄에서 시작하고, 옆에 요소를 허용하지 않음. \(float 제\) | 다른 콘텐츠와 함께 흐르고, 옆에 있는 것 허 | 불가능. 설정 시 무시됨. |
| `vertical-align` 정렬 가능 여 | 불가능 | 불가능 | 불가능 |
| margin, padding | 모든 방향에서 가능 | 모든 방향에서 가능 | 수평만 가능. 수직은 `line-height`에 의존 |
| float | - | - | 수직 마진과 패딩을 설정할 수 있는 블록 엘리먼트와 같음. |

#### `relative`, `fixed`, `absolute` 와 `static` 요소의 차이점

* static
  * 기본 위치. 
  * 요소는 평소와 같이 페이지에 위치. 
  * top, right, bottom, left, z-index 속성은 적용 불가능
* relative
  * 요소의 위치는 레이아웃을 변경하지 않고 상대적으로 조정됨
  * 배치되지 않은 요소의 간격을 남겨둠
* absolute
  * 요소는 페이지의 평소 위치에서 제거되고 가장 가까운 위치에 relative 부모 블록이 있는 경우 지정된 위치에 배치됨. 
  * 그렇지 않으면 최상위 블록과 관련됨. 
  * 여백을 가질 수 있으며 다른 여백과 충돌하지 않음. 
  * 다른 요소의 위치에 영향을 주지 않음.
* fixed
  * 요소는 페이지의 평소 위치에서 제거되고 뷰포트를 기준으로 지정된 위치에 배치
  * 스크롤 할 때 이동하지 않음.
* sticky
  * relative 와 fixed 의 하이브리드. 
  * 요소는 지정된 임계 값을 넘을 때까지 상대적 위치로 처리되며, 
  * 특정 지점에서 고정된 위치로 처리.

#### **반응형 웹사이트**를 코딩하는 것과 모바일 퍼스트를 사용하는 것의 차이는?

반응형 웹을 만드는 것은 일부 요소가 미디어 쿼리를 통해 너비나 기능 등이 조정되는 것을 말함

```css
@media (min-width: 601px) { 
  .my-class { 
    font-size: 24px;
  }
}
@media (max-width: 600px) {
  .my-class { 
    font-size: 12px;
  }
}
```

모바일 퍼스트도 마찬가지로 미디어쿼리를 사용하지만, 모바일을 먼저 정의

```css
.my-class { 
  font-size: 12px;
}

@media (min-width: 600px) {
  .my-class { 
    font-size: 24px;
  }
}
```

모바일 퍼스트는 모든 스타일 규칙에 대해 유효성 검사를 받을 필요가 없으므로, 모바일에서 더 뛰어난 성능을 발휘하고, 반응형 규칙보다 더 명확한 코드를 작성해야 한다.

#### 레티나 디스플레이에 적용하려면?

* 가장 좋은 방법은 미디어쿼리`@media only screen and (min-device-pixel-ratio : 2) {...}`를 이용하여 `background-image`를 변경하는 것
* 아이콘의 경우 svg 혹은 아이콘 폰트를 사
* 다른 방법으로 `window.deviceFixeLatio`값 확인 후, `img src` 속성을 더 높은 해상도 버전으로 대체하는 스크립트를 사용하는 것.

#### `absolute` 포지셔닝 대신 `translate()`를 사용하는 이유

브라우저 성능의 문제로 볼 수 있음.`transform`이나 `opacity`를 변경하면 브라우저의 **리플로우**나 **리페인트**가 트리거되지 않고 컴포지션만 실행되는 반면, 절대 위치 값을 변경하면 '**리플로우**'가 발생한다.

`transform`을 사용하면 브라우저에서 이 요소에 위한 GPU 레이어를 생성하지만, 포지션 위치 속성 변경은 CPU를 사용한다. 그러므로 `translate()`가 더 효율적이며 매끄러운 애니메이션을 위한 페인트 시간이 짧아진다.

#### 블럭 내 자식 요소를 중앙 정렬하는 방법은?

```css
div {
  display: block;
  margin:0 auto;
}
```

#### 콘텐츠를 숨기는 방법들 **스크린 리더**에서 접근가능한 방법은?

* `display: none;` 
  * 영역 자체가 없어지면서 콘텐츠를 숨김.
* `visibility: hidden;`
  * 영역은 존재하지만 콘텐츠만 숨김.
* box요소를 작게 만들고 숨김. `width: 0; height: 0; overflow: hidden;`
  * 스크린 리더에서 접근가능한 방법은 이 방법이 적합
* `text-indent, position` 등에 음수 지정


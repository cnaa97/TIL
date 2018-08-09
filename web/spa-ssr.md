---
description: SPA (Single Page Application) vs SSR (Server Side Rendering)
---

# SPA, SSR 비교

|  | SPA \(Single Page Appliation\) | SSR \(Server Side Rendering\) |
| :--- | :--- | :--- |
| 랜더링 | 정적 소스를 한 번에 다운받아, 클라이언트에서 랜더링하는 방법  | 페이지를 이동할 때마다 모든 리소스를 다운받는 방식 |
| 초기 구동 속 | 페이지 이동 시 필요한 리소스만 다운받기 때문에 빠르지만, 초기 구동 시 상대적으로 느린 단점. \(Code Split 등의 방법으로 해결 가능\)  | 상대적으로 빠르지만, 페이지마다 리소스를 다운받아야 하기 때문에  |
| 라우 | 클라이언트 사이드에서 결정됨. hash, browserHistory 사용  | 서버에서 정의 |
| SEO | 어플리케이션이라면 큰 문제는 아니지만, 클라이언트 랜더링 방식에서 SEO는 단점이다. \(라이브러리에서 지원하는 SSR 등의 방법 이용가\) | 문제 없음   |


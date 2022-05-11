# Front-end Framework 필요성

- 웹 페이지 기능이 많아짐, 사용자 눈이 높아짐
- 개발 코드량 많아지고, 사용자의 클릭이 많아졌음



- Component 단위로 조립식으로 웹페이지 UI 개발(생산성, 가동성 UP)
- Virtual DOM : JQuery의 비효율적 DOM 제어 개선(웹페이지 성능 UP)

## Framework 별 특징

- angular
  - 프레임워크
  - 양방향 바인딩
- react
  - 라이브러리
  - 가상돔
- vue
  - 프레임워크
  - 양방향 바인딩 + 가상돔
- svelte
  - 가상돔x
  - 적은 코드
  - 강력한 반응형 개발



> Framework VS Library
> **제어권의 역전**
>
> - Framework: 제어권이 프레임워크에
> - Library: 제어권이 개발자에게



# Vue.js

- Progressive JavaScript Framework
- javascript 프로젝트에서 점진적으로 수정해 나가면서 Vue.js를 적용시킬 수 있다. 
  - vue를 적용하기 위해 완전히 뒤엎는 것이 아닌, 수정하는 방식으로 적용하는 프레임워크
- 현대적인 tool과 다양한 라이브러리를 통해 SPA를 완벽하게 지원

> [참고] Evan You - 2014
>
> - Angular 개발자 출신
> - Angular보다 가볍고 간편하게 사용할 수 있는 프레임워크 => Vue.js



## SPA

- Single Page Application
- 현재 페이지를 동적으로 렌더링

- 서버로부터 최초에만 페이지 다운로드하고 이후에는 동적으로 DOM을 구성
- 연속되는 페이지 간의 사용자 경험(UX)을 향상
  - 모바일 사용량 증가
  - 트래픽의 감소와 속도, 사용성, 반응성이 중요
- 동작 원리의 일부가 CSR의 구조를 따름

### SPA 등장 배경

- 과거 웹 사이트들은 요청에 따라 매번 새로운 페이지를 응답(MPA)
- 스마트폰 등장 => 모바일 최적화 필요성 대두
- 이러한 문제를 해결하기 위해 Front-End 프레임워크들 등장
  - CSR< SPA 등장
- 1개의 웹 페이지에서 여러 동작이 이루어지며 모바일 앱과 비슷한 형태의 사용자 경험을 제공



### CSR

- Client Side Rendering
- 클라이언트에서 화면을 구성

- 최초 요청 시 HTML, CSS, JS 등 데이터를 제외한 각종 리소스를 응답받고 이후 클라이언트에서 필요한 데이터만 요청해 JS로 DOM을 렌더링하는 방식
- 즉, 처음엔 뼈대만 받고 브라우저에서 동적으로 DOM을 그림
- SPA가 사용하는 렌더링 방식

![CSR](https://miro.medium.com/max/1400/1*CRiH0hUGoS3aoZaIY4H2yg.png)

출처: https://medium.com/walmartglobaltech/the-benefits-of-server-side-rendering-over-client-side-rendering-5d07ff2cefe8



- 장점
  1. 서버 - 클라이언트 간 트래픽 감소
  2. 사용자 경험 향상
- 단점
  1. SSR에 비해 전체 페이지 렌더링 시점이 느림
  2. SEO(검색 엔진 최적화)에 어려움이 있음 (최초 문서에 데이터가 없기 때문에)



###  SSR

- Server Side Rendering
- 서버에서 클라이언트에게 보여줄 페이지를 모두 구성하여 전달
- JS 웹 프레임워크 이전에 사용되던 전통적인 렌더링 방식

![SSR](https://miro.medium.com/max/1400/1*jJkEQpgZ8waQ5P-W5lhxuQ.png)

출처: https://medium.com/walmartglobaltech/the-benefits-of-server-side-rendering-over-client-side-rendering-5d07ff2cefe8

- 장점

  1. 초기 구동 속도가 빠름
     - 클라이언트가 빠르게 컨텐츠 볼 수 있음

  2. SEO에 적합
     - DOM에 이미 모든 데이터가 작성되어 있음

- 단점

  - 모든 요청마다 새로운 페이지를 구성하여 전달
    - 반복되는 전체 새로고침으로 인해 사용자 경험이 떨어짐
    - 상대적으로 트래픽이 많아 서버의 부담이 클 수 있음



### SSR & CSR

- 두 방식의 차이는 렌더링의 주최가 누구인가에 따라 결정
- 렌더링을 
  - 서버가 한다 => SSR
  - 클라이언트가 한다 => CSR
- 어떤 것이 좋다가 아니라
  서비스, 프로젝트에 따라 적절하게 또는 섞어서 구성



### [참고] SEO

- Search Engine Optimization
- 웹 페이지 검색엔진이 자료를 수집하고 순위를 매기는 방식에 맞게
  웹 페이지를 구성해서 검색 결과의 상위에 노출될 수 있도록 하는 작업
- 인터넷 마케팅 방법 중 하나
- 구글의 등장 이후 검색엔진들이 컨텐츠의 신뢰도를 파악하는 기초 지표로 사용됨
  - 다른 웹 사이트에서 얼마나 인용되었나를 반영
  - 결국 타 사이트에 인용되는 횟수를 늘리는 방향으로 최적화

- [구글 SEO 기본 가이드](https://developers.google.com/search/docs/beginner/seo-starter-guide?hl=ko#areyouongoogle)



### [참고] SEO 대응

- Vue, React 등의 SPA 프레임워크, 라이브러리는 SSR을 지원하는 SEO 대응 기술이 이미 존재
  - SEO 대응이 필요한 페이지에 대해서는 선별적 SEO 대응 가능
- 혹은 추가로 별도의 프레임 워크 사용가능
  - Nuxt.js
    - Vue.js 응용 프로그램을 만들기 위한 프레임워크
    - SSR 지원
  - Next.js
    - React 응용 프로그램을 만들기 위한 프레임워크
    - SSR 지원



## Why Vue.js

- 페이지 규모가 커지면서 사용하는 데이터도 늘어나고 사용자와의 상호작용도 많이 이루어짐

- Vanilla JS만으로는 관리하기가 어려움

  - 예시) 페이스북 친구가 이름을 수정했을 경우

    -> 화면상에서 타임라인의 이름, 메시지 상의 이름, 주소록에서의 친구 이름 등 변경되어야 할 게 많음



### 비교

- Vanilla JS
  - 어떤 유저가 100만개의 게시글을 작성
  - 이 유저가 닉네임을 변경하면 100만 개 모두 수정
  - '모든 요소'를 선택해서 '이벤트'를 등록하고 값을 변경해야 함
- Vue.js
  - DOM과 Data가 연결되어 있으면 
  - Data를 변경하면 이에 연결된 DOM은 알아서 변경됨
  - 개발자는 Data에 대한 관리만 신경쓸 수 있음
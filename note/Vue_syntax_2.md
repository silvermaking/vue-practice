# 02. Template Syntax

## Directive

### v-for

- 원본데이터를 기반으로 엘리먼트 또는 템플릿 블록을 여러 번 렌더링
- item in items 구문 사용
- item 위치의 변수를 각 요소에서 사용할 수 있음
  - 객체의 경우 key
- v-for 사용시 반드시 key 속성을 각 요소에 작성([DOC](https://kr.vuejs.org/v2/style-guide/#v-for-%EC%97%90-key-%EC%A7%80%EC%A0%95-%ED%95%84%EC%88%98))
- v-if와 v-for을 동시에 사용하는 것 지양(v-for가 우선순위가 높음)
  - [DOC](https://kr.vuejs.org/v2/style-guide/#v-if%EC%99%80-v-for%EB%A5%BC-%EB%8F%99%EC%8B%9C%EC%97%90-%EC%82%AC%EC%9A%A9%ED%95%98%EC%A7%80-%EB%A7%88%EC%84%B8%EC%9A%94-%ED%95%84%EC%88%98)
  - [practice](../practice/01_intro/99_if_for.html)

- [practice](../practice/01_intro/03_v-for.html)


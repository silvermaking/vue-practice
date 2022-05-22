# 01. Basic syntax of Vue.js

## Vue Instance

- 모든 Vue 앱은 Vue 함수로 새 인스턴스를 만드는 것부터 시작

```javascript
const app = new Vue({

})
```

- Vue 인스턴스를 생성할 때는 Options 객체({})를 전달해야 함
- Options들을 사용하여 우너하는 동작을 구현
  - el, data, methods 등
- Vue instance = Vue component



## Options/DOM - 'el'(element)

```javascript
const app = new Vue({
	el: '#app'
})
```

- Vue 인스턴스에 마운트(연결) 할 기존 DOM 엘리멘트가 필요
- CSS 선택자 문자열 혹은 HTML Element로 작성
- new를 이용한 인스턴스 생성 때만 사용



## Options/Data - 'data'
```javascript
const app = new Vue({
	el: '#app'
    data: {
    message: 'Hello',
	}
})
```

- Vue 인스턴스의 데이터 객체
- Vue인스턴스의 상태 데이터를 정의하는 곳
- Vue template에서 interporlation을 통해 접근 가능
- v-bind, v-on과 같은 directive에서도 사용 가능
- Vue 객체 내 다른 함수에서 this 키워드를 통해 접근 가능
- [주의]
  - 화살표 함수를 'data'에서 사용하면 안 됨
  - 화살표 함수가 부모 컨텍스트를 바인딩하기 때문에, 'this'는 예상과 달리 Vue 인스턴스를 가리키지 않음



## Options/Data - 'methods'
```javascript
const app = new Vue({
	el: '#app'
    data: {
    message: 'Hello',
	},
    methods: {
      greeting function () {
    	console.log('hello')
	  }
   }
})
```

- Vue 인스턴스에 추가할 메서드
- Vue template에서 interpolation을 통해 접근 
- v-on과 같은 directive에서도 사용 가능
- Vue 객체 내 다른 함수에서 this키워드를 통해 접근 가능
- [주의]
  - 메서드를 정의하는데 화살표 함수 사용하면 안 됨
  - 화살표 함수가 부모 컨텍스트를 바인딩하기 때문에, 'this'는 Vue 인스턴스가 아니며 'this.message'는 정의되지 않음

> This
>
> - [DOC](https://kr.vuejs.org/v2/api/#data)
> - vm.$data.message == vm.message 동일

---

# 02. Template Syntax

- 렌더린 된 DOM을 기본 Vue 인스턴스의 데이터에 선언적으로 바인딩할 수 있는 HTML 기반 템플릿 구문을 사용
  1. Interpolation
  2. Directive

## Directive

- [DOC](https://kr.vuejs.org/v2/api/#%EB%94%94%EB%A0%89%ED%8B%B0%EB%B8%8C)

- v-접두사가 있는 특수 속성
- 속성 값은 단일 JS 표현식이 됨 (v-for는 예외)
- 표현식의 값이 변경될 때 반응적으로 DOM에 적용하는 역할
  - 전달인자(Arguments)
    - `:` (콜론)을 통해 전달인자를 받을 수 도 있음
  - 수식어(Modifiers)
    - `.` (점)으로 표시되는 특수 접미사
    - directive를 특별한 방법으로 바인딩 해야 함을 나타냄

### v-text

- 엘리먼트의 textContent를 업데이트
- 내부적으로 interpolation 문법이 v-text로 컴파일 됨

- [practice](../practice/01_intro/03_v-text.html)

### v-html

- 엘리먼트의 innerHTML을 업데이트
  - XSS 공격에 취약할 수 있음
  - [참고](https://velog.io/@raram2/%EB%8B%B9%EC%8B%A0%EC%9D%B4-innerHTML%EC%9D%84-%EC%93%B0%EB%A9%B4-%EC%95%88%EB%90%98%EB%8A%94-%EC%9D%B4%EC%9C%A0)
- 임의로 사용자로부터 입력 받은 내용은 v-html에 '절대' 사용 금지
- [practice](../practice/01_intro/03_v-html.html)

### v-show

- 조건부 렌더링
- 엘리먼트는 항상 렌더링 되고 DOM에 남아있음
- 단순히 엘리먼트에 display CSS 속성을 토글하는 것
  - 예) display: none
- [practice](../practice/01_intro/03_v-show.html)

### v-if, v-else-if, v-else

- 조건부 렌더링
- 조건에 따라 블록을 렌더링
- directive의 표현식이 true일 때만 렌더링
- 엘리먼트 및 포함된 directive는 토글하는 동안 삭제되고 다시 작성됨
- [practice](../practice/01_intro/03_v-if.html)



> v-show VS v-if

- **v-show** (Expensive initial load, cheap toggle)
- **v-if**(Cheap initial load, expensive toggle)


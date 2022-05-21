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



### v-on

- 엘리먼트에 이벤트 리스너 연결
- 이벤트 유형은 전달인자로 표시함
- 특정 이벤트가 발생했을 때, 주어진 코드가 실행 됨
- 약어
  - "@"
- [practice](../practice/01_intro/03_v-on.html)



### v-bind

- HTML 요소의 속성에 Vue의 상태 데이터를 값으로 할당
- Object 형태로 사용하면 value가 true인 key가 class 바인딩 값으로 할당
- 약어(Shorthand)
  - ":" 콜론
- [practice](../practice/01_intro/03_v-bind.html)



### v-model

- HTML form 요소의 값과 data를 양방향 바인딩
- 수식어
  - .lazy
    - input 대신 change 이벤트 이후에 동기화
  - .number
    - 문자열을 숫자로 변경
  - .trim
    - 입력에 대한 trim을 진행
- IME(중,일,한)가 필요한 언어([DOC](https://kr.vuejs.org/v2/guide/forms.html))
  - input v-on이벤트 사용
- [practice](../practice/01_intro/03_v-model.html)



## Options/Data - 'computed'

- 데이터를 기반으로 하는 계산된 속성
- 함수의 형태로 정의하지만 함수가 아닌 함수의 반환 값이 바인딩 됨
- 종속된 데이터에 따라 저장(캐싱)됨
- **종속된 데이터가 변경될 때만 함수를 발생**
- 즉, 어떤 데이터에도 의존하지 않는 computed 속성의 경우 절대로 업데이트되지 않음
- 반드시 반환 값이 있어야 함
- [practice](../practice/01_intro/04_computed.html)

### computed & methods

- computed 속성 대신 methods에 함수를 정의할 수도 있음
  - 최종 결과에 대해 두 가지 접근 방식은 서로 동일
- 차이점은 computed 속성은 종속 대상을 따라 저장(캐싱) 됨
- 즉, computed는 종속된 대상이 변경되지 않는 한 computed에 작성된 함수를 여러 번 호출해도 계산을 다시 하지 않고 계산되어 있던 결과를 반환
- 이에 비해 methods를 호출하면 렌더링을 다시 할 때마다 항상 함수를 실행
- [practice](../practice/01_intro/04_computed_methods.html)

```html
  <div id="app">
    <p>원본 메시지: "{{ message }}"</p>
    <!-- computed는 계산 된 값을 사용 -->
    <p>computed: "{{ reversedMessageComputed }}"</p>
    <!-- methods는 함수(메서드)를 호출 -->
    <p>methods: "{{ reversedMessageMethod() }}"</p>
  </div>

  <script>
    const app = new Vue({
      el: '#app',
      data: {
        message: '안녕하세요'
      },
      computed: {
        reversedMessageComputed: function () {
          return this.message.split('').reverse().join('')
        }
      },
      methods: {
        reversedMessageMethod: function () {
          return this.message.split('').reverse().join('')
        }
      }
    })
  </script>
```



## Options/Data - 'watch'

- 데이터를 감시
- 데이터에 변화가 일어났을 때 실행되는 함수
- [practice](../practice/01_intro/04_watch.html)
- 데이터 이름으로 함수 정의

```html
  <div id="app">
    <p>{{ num }}</p>
    <button @click="num += 1">add 1</button>
  </div>
  
  <script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
  <script>
    const app = new Vue({
      el: '#app',
      data: {
        num: 2,
      },
      watch: {
        num: function () {
          console.log(`${this.num}이 변경되었습니다.`)
        }
      },
    })
```



### computed * watch 

[DOC](https://kr.vuejs.org/v2/guide/computed.html#computed-%EC%86%8D%EC%84%B1-vs-watch-%EC%86%8D%EC%84%B1)

- computed
  - 특정 데이터를 **직접적으로** 사용/가공하여 다른 값으로 만들 때 사용
  - 속성은 계산해야 하는 목표 데이터를 정의하는 방식으로
    소프트웨어 공학에서 이야기하는 '선언형 프로그래밍' 방식
  - 특정 값이 변동하면 **해당 값을 다시 계산해**서 보여준다.

- watch
  - 특정 데이터의 변화 상황에 맞춰 **다른 data 등이 바뀌어야 할 때 주로 사용**
  - 감시할 데이터를 지정하고 그 데이터가 바뀌면 특정 함수를 실행하는 방법
  - 소프트웨어 공학에서 이야기하는 '명령형 프로그래밍' 방식
  - 특정 값이 변동하면 **다른 작업**을 한다.
  - 특정 대상이 변경되었을 때 콜백 함수를 실행시키기 위한 트리거
- computed와 watch는 어떤 것이 더 우수한 것이 아닌 사용하는 목적과 상황이 다름
- [practice](../practice/01_intro/04_computed_watch.html)



> 선언형 & 명령형
>
> - 선언형: 계산해야 하는 목표 데이터를 정의(computed)
> - 명령형: 데이터가 바뀌면 특정 함수를 실행해!(watch)



## Optinos/Assets - 'filters'

- 텍스트 형식화를 적용할 수 있는 필터
- interpolation 혹은 v-bind를 이용할 때 사용 가능
- 필터는 JS 표현식 마지막에 "|" (파이프)와 함께 추가되어야 함
- 이어서 사용(chaining) 가능
- [practice](../practice/01_intro/05_filters.html)

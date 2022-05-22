# 03. Lifecycle Hooks

- 각 Vue 인스턴스는 생성될 때 일련의 초기화 단계를 거침
  - 예를 들어 
    - 데이터 관찰 설정이 필요한 경우,
    - 인스턴스를 DOM에 마운트
    - 데이터가 변경되어 DOM을 업데이트하는 경우 등
- 그 과정에서 사용자 정의 로직을 실행할 수 있는 Lifecycle Hooks도 호출됨



![lifecycle](https://dltqhkoxgn1gx.cloudfront.net/img/posts/how-to-use-lifecycle-hooks-in-vue3-1.png)

https://learnvue.co/2020/12/how-to-use-lifecycle-hooks-in-vue3/#what-are-the-vue-lifecycle-hooks



- 예를 들어 **created hook**은 vue 인스턴스가 생성된 후에 호출 됨
- [practice](../practice/01_intro/06_lifeCycleHooks.html)

```javascript
const app = new Vue({
    el: "#app",
    data: {
        imgSrc: "",
    },
    methods: {
        getImg: function () {
            axios.get(API_URL).then((response) => {
                this.imgSrc = response.data.message;
            });
        },
    },
    // lifecycle hook : created
    created: function () {
        this.getImg();
    },
});
```





# 04. lodash library

- https://lodash.com/

- 모듈성, 성능 및 추가 기능을 제공하는 JS 유틸리티 라이브러리
- array, object 등 자료구조를 다룰 때 사용하는 유용하고 간편한 유틸리티 함수들을 제공
- 함수 예시
  - `reverse`, `sortBy` , `range`, `random` ...

- [practice](../practice/01_intro/99_lodash.html)

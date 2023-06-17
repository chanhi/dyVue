# Web Frontend

## dongyanh

#### vue.js Documents

https://v3-docs.vuejs-korea.org/guide/essentials/template-syntax.html

#### CDN방식 import

```
<script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
```

## 기본 구조

```html
<script>
  new Vue({
      el: '#appID',
      data: {
          myData: 'data',
      },
      methods: {
          myFunc: function() {
              ...
          },
      }
  })
</script>
```

## 데이터 바인딩(data binding)

- {{myData}}
  - {{myData + data?}} 이런 식으로 javascript 표현식 사용 가능
  - 단 하나의 표현식만 쓸 수 있다.
- v-text="myData"
- v-html="myData"
- javascript 표현식 사용

```html
{{ number + 1 }} {{ ok ? '예' : '아니오' }} {{
message.split('').reverse().join('') }}

<div :id="`list-${id}`"></div>
```

## 함수(function)

```html
<button v-on:click="countUp(1)">1씩증가</button>
<input type="text" @input="textModifier" />
```

methods: { countUp: function(value) { this.count+=value; }, textModifier:
funtion(event) { printf(event.target.value); } //이런식으로 js사용해서 실시간
데이터 입력값 전달 가능 }

- `methods` 에 구현
- parameter(인자) 전달 가능

## 이벤트

- v-on
  - 속성을 사용하기 위해서 `v-on:attr` 이런식으로 사용한다
  - 이것은 축약해서 `@attr` 이렇게 사용할 수 있다

```html
<button v-on:click="countUp">Count up</button>
<button @click="countDown">Count down</button>
```

## 반복문

- v-for
  -     v-for="(value, key, index)"//위의 인자 순서대로 값, 키, 인덱스가 들어온다. 이름은 상관 없음
  - value, key, index 는 별칭으로 사용한다.

```html
<li v-for="(value, key, index) in $data">{{index}}.{{key}} : {{value}}</li>
```

## 조건문

- v-if
  - 참일 때 실행

## 속성 바인딩

- v-bind
  - 태그의 속성을 동적으로 사용

```html
<div v-bind:id="dynamicId"></div>
<p :class="myClass">클래스 v-bind로 지정</p>
<p :class="[myClass, darkClass]">복수의 클래스 v-bind로 지정</p>
<p :style="{color: myColor}">문자색 v-bind로 지정</p>
<img v-bind:src="filename" />
<img :src="filename" />
```

## 입력 바인딩

- v-model
  - 입력 태그에 동적인 데이터를 사용
  - input, textarea, select, form...

```html
<input v-model="myName" placeholder="Your Name" />
<p>Your name is {{myName}}</p>
<textarea v-model="myText" cols="30" rows="10"></textarea>
<p>Text: {{myText}}</p>
<p>Text length: {{myText.length}}</p>
```

<img src="/imges/README1.png" width="700px">

## computed, watch

#### computed

- 너무 많은 연산을 템플릿 안에서 하면 코드가 비대해지고 유지보수가 어렵다.
- computed 속성은 종속 대상을 따라 저장(캐싱)
- computed 속성은 해당 속성이 종속된 대상이 변경될 때만 함수를 실행

#### watch

- 데이터 변경에 대한 응답
- 비동기식 또는 시간이 많이 소요되는 조작을 수행하려는 경우에 가장 유용

## vue application

#### vue-cli
- Vue Command Line Interface
- ```npm install -g @vue/cli``` : 글로벌로 설치
- ```vue create project_name``` : project_name을 가진 vue 프로젝트 생성
  - default 생성: babel, eslint
  - manually 옵션 생성: router, vuex 등 추가 가능 (Typescript..)
  - ```vue ui``` : GUI 생성(프로젝트 매니저)
* ```Set-ExecutionPolicy -ExecutionPolicy RemoteSigned``` : 권한 오류 발생 시 권한 설정
- ```cd /project_name``` : 생성된 프로젝트로 이동
  - ```npm run serve``` : 프로젝트 실행
  - ```npm run lint -- --fix``` : fix 관련 오류 발생 시(eslint에 의한 문법 맞춤)
- view 표현 방법
```html
<template>
  <div class="test">
      <h1>{{title}}</h1>
      <h2 v-html="htmlText"></h2>
  </div>
</template>

<script>
export default {
  data () {
    return {
      title: 'Test Page',
      htmlText: '<p style="color:blue">v-html</p>'
    }
  }
}
</script>
```
-프로젝트 파일 구조
  - node_modules: vue를 실행하기 위한 모듈을 모아둔 폴더
  - public : 실제 웹에서 보이는 부분
  - src : 프로젝트를 구성하는 실질적인 폴더
    - assets : 이미지, 파비콘과 같은 콘텐츠를 저장하는 폴더
    - componets: 여러개의 콘텐츠 컴포넌트로 분할
    ```
    <template>
      <div></div>
    </template>
    <script>
      export default {
        name: '', //컴포넌트 이름
        components: {}, //외부 컴포넌트 import 후 이곳에 등록하여 사용
        data() {
          return {}; //변수 생성, 생성된 변수는 this를 통해 접근
        },
        setup() {}, //컴포지션 api
        created() {}, //컴포넌트가 생성되면 실행
        mounted() {}, //탬플릿에 작성한 html코드가 랜더링 된 후 실행
        unmounted() {}, //컴포넌트를 빠져나갈 때 실행
        methods: {} //컴포넌트 내에서 사용할 메도스 정의
    </script>
    ```
      - 재사용 가능(동일 기능을 컴포넌트화 하여 재사용)
      - 
      - snippet: 등록된 코드를 단축키를 이용해 바로 사용하는 기능
      - Vue.json 피일에 코드를 등록```"prefix": "snippet_name", "body": [내용], "description": 설명```
    - views: 보여지는 부분
    - router: 보여질 view 경로 설정
    - store: Vuex를 통해 사용하는 전역변수 저장소
    - App.vue: 최종적으로 보여줄 메인 페이지, 각 컴포넌트와 뷰를 임포트하여 보여줌
    - main.js: 가장 상위 js파일(vue, router, store 사용 선언과 createApp을 통한 앱 생성)
  -package.json: 설치된 의존성 패키지, 실행 스크립트, 프로젝트 이름 등 설정과 패키지에 대한 정보가 담겨있다
  
 ## 프로젝트 구상

 * Vuetify: vue 탬플릿
 * https://madewithvuejs.com/
 * 음악 스트리밍 사이트
 * 영화 사이트
 * 옷 사이트
 * 포트폴리오

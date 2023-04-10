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
... methods: { countUp: function(value) { this.count+=value; }, textModifier:
funtion(event) { printf(event.target.value); } //이런식으로 js사용해서 실시간
데이터 입력값 전달 가능 }
```

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

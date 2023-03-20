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
            }
            methods: {
                myFunc: function() {
                    ...
                },
            }
        })
</script>
```

## 데이터 바인딩(data binding)
* {{myData}}
* v-text="myData"
* v-html="myData"

## 이벤트
* v-on

v-on:click
@click

## 반복문
* v-for

## 속성 바인딩
* v-bind
```html
<img v-bind:src="filename">
<img :src="filename">
```

## 입력 바인딩
* v-model

<img src="/imges/README1.png" width="700px">

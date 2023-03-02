##### :cactus: Vue3 -part2

 
## 부모 --> 자식 데이터 전달 
부모 컴포넌트로부터 자식 컴포넌트로 어떤 속성의 값을 전달하려고 할때 어떻게 할까?  2가지 방법의 차이를 살펴보자.  

1. <b> props </b>로 데이터 전달 :모든 컴포넌트 인스턴스에는 각자의 범위(scope)가 있다. 상위 컴포넌트가 하위 컴포넌트로 데이타를 전달하고자 할때 <b>props</b> 라는것을 이용한다. 반대로 하위 컴포넌트에서 상위 컴포넌트로 데이터를 전달하고자 할때는 <b>Emit</b>라는 것을 사용한다. 잘 기억해두자. 
<img width="240" alt="스크린샷 2023-03-02 오전 10 57 22" src="https://user-images.githubusercontent.com/48478079/222311016-9ad2c66f-15be-4520-b16b-196be1c3099d.png">

a. 일반 vue객체에서 데이터를 전달하는 방식(우리가 실습하면서 많이 했던 방식)과  
b. 컴포넌트 내에서 데이터의 전달방식이 어떻게 다른지  

### 앞에서 했던 방식으로 data()문을 사용하는 것이다.  
``` javascript
~
data(){
  return {
     comments:'회원가입 | 로그인'
     }
  },
~ ~
```
그럼 b.에 속한 방식은 어떤 모양일까  
```javascript 
export default{
props : [ 'Kebab-case'로 작성하고 배열로 표현 ],
data(){
     
   }
```  
일단 모양을 익혀두자. 좀더 언급해야 할것이 있지만 나중에 다시 살펴보자.

### 이제 a. , b.의 방식으로 살펴보자.
vue-cli-실행4 의 예제를 갖고 해보자. Modal.vue의 내용을 아래처럼 변경해보자.
```html
<template>
  <div class="backdrop"> 
    <div class="modal">
      <h2>{{ comments  }}</h2>
      <p> Modal content</p>
    </div>
  </div>
</template>
```   
여기서 
'comments'가 어디로부터 오는가를 볼것이다.  같은 Modal.vue파일에서 
```javascript
<script>
export default {
  data(){
    return {
      comments:'회원가입 | 로그인'
    }
  }
}
</script>
```
<img width="258" alt="스크린샷 2023-03-02 오전 11 39 29" src="https://user-images.githubusercontent.com/48478079/222317012-fe5df019-3c79-414a-933b-161837869b50.png">


와 같이 출력된다. 이제 props를 사용해서 같은 결과를 얻어보자. props 는 상위컴포넌트에서 하위 컴포넌트로 데이터를 전달할때 사용한다는 것을 기억할 것이다. 그래서 App.vue와 Modal.vue의 내용을 바꿔야 한다.  

[App.vue] 

```html
<template>
  <h1>{{ title }}</h1>
  <p>created by Vue3</p>
 <Modal comments="회원가입 | 로그인"/>
</template>
```

[ Modal.vue ]
```html
<template>
  <div class="backdrop"> 
    <div class="modal">
      <h2>{{ comments}}</h2>
      <p> Modal content</p>
    </div>
  </div>
</template>

<script>
export default {
  props:[ 'comments']
}
</script>

```   
props를 이용하여 다른 것도 전달해보자.  

[App.vue] 

```html
<template>
  <h1>{{ title }}</h1>
  <p>created by Vue3</p>
 <Modal comments="회원가입 | 로그인" text="가입혜택이 있습니다"/>
</template>
```

[ Modal.vue ]
```html
<template>
  <div class="backdrop"> 
    <div class="modal">
      <h2>{{ comments}}</h2>
      <p> Modal content</p>
      <span> {{ text }}</span>
    </div>
  </div>
</template>

<script>
export default {
  props:[ 'comments' ,'text']
}
</script>

```  

## 바인딩을 활용해서 사용해보자   






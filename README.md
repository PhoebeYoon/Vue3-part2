##### :cactus: Vue3 -part2

## vue의 [ref] 속성 사용하기

ref란 뷰에서 컴포넌트 또는 DOM에 접근하기 위해 사용하는 속성입니다.  마운트된 요소에만 적용가능합니다. 마운트 되지 않은 요소에 사용하면 ref undefined가 발생합니다. 접근하고자 하는 태그에 <b>ref="이름" </b> 속성 명시하고 사용시에는  <b> this.$refs.이름 </b> 
 
 
App.vue 파일의 내용을 수정한다.  
```html
<template>
  <h1>{{  title  }}</h1>
  <input type="text" ref="inputbox">
  <button @click="handleClick">Click me</button>
</template>

<script>
export default {
  name :'App',
  data() {
    return {
      title :'My Frist Vue App ;)'
    }
  },
  methods:{
    handleClick(){
      console.log(this.$refs.inputbox)
    }
  }
}
</script>
```
버튼을 클릭하면 콘솔창에 ``` <input type="text">  ``` 라고 출력된다. 
이 ref 속성은 마치 자바스크립트에서 DOM에 있는 html 태그를 읽어올때 사용했던 document.getElementsByTagName 이나 querySelector와 마찬가지로 작동한다. 

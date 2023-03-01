##### :cactus: Vue3 -part2

## 이제 간단한 컴포턴트를 등록하고 사용해보자.  
 [ /components/Modal.vue ]
 
 ```html
<template>
  <div class="backdrop"> 
    <div class="modal">
      <p> Modal content</p>
    </div>
  </div>
</template>
<style>
.modal {
  width:400px; padding:20px; margin:100px auto;
  background: white;
  border-radius: 10px;
}
p { color:hotpink; font-size: 120%; }
.backdrop{ top:0; position: fixed;
  background: rgba(0,0,0,0.5);
  width: 100%;  height: 100%;}
</style>

```
 
 
 [ App.vue ]
 ```html
<template>
  <h1>{{ title }}</h1>
  <p>created by Vue3</p>
 <Modal />
</template>

<script>
import Modal from './components/Modal.vue'
// Modal.vue 삽입하고
export default {
  name :'App',
  components :{ Modal}, 
  data(){
    return {
       title :"My First Vue Application"
    }
  }
}
</script>
<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
body { margin: 0;}
h1 { border-bottom: 2px dashed #000; 
  padding-bottom:10px; display:inline}
</style>
```
 
1) import Modal from './components/Modal.vue' 컴포넌트를 불러오고,  
2) components :{ Modal},  컴포넌트를 등록하고,   
3) <Modal />  컴포넌트를  태그처럼 사용
  
여기까지 잘 작성되었다면 결과화면은  
<img width="330" alt="스크린샷 2023-03-01 오후 10 35 14" src="https://user-images.githubusercontent.com/48478079/222154090-4b73ce2e-1147-4c1c-b4d1-19b62073eea6.png">
   와 같을 것이다. 그런데 여기서 눈여겨볼것중 하나는  
Modal.vue에 적용된 p태그 스타일인 App.vue 에 있는 p태그에도 적용되었다는 것이다. 그래서 'created by Vue3' 와 "Modal content'가 모두 분홍색이다.  
Modal.vue파일의 ``` <style scoped>  ``` 처럼 scoped 를 추가하면 이 스타일은 오직 해당 파일안에서만 적용된다는 것을 알 수 있다 


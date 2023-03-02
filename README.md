##### :cactus: Vue3 -part2


프로젝트가 생성되면 ``` <div id="app"> ```안에 모든 내용이 들어가게된다. 모달창, 로그인창, 팝업창 등등. 그러면 이런 것들은 기존에 있던것들 위 즉 최상위로 올라와야 하는데 구조가 복잡해지면 모달을 띄우기가 쉽지 않을 것이다. 그래서 이런것을 해결해주는 것이 teleport이다. 이것은 React에서 다루는 portal과 동일한 기능이다.  

## teleport란
텔레포트는 index.html 안에 ```<div id="app">```과 같은 레벨의 별개의 div를 만드는 것이다. vue_slot에 사용했던 내용을 가지고 해보자.  

[index.html] 
```html
<div id="app"></div>
<div class="modal"></div>

```
[App.vue]
```html
<template>
  <h1>{{ title }}</h1>
  <p>created by Vue3</p> 
    <div v-if="showModal"  > <!-- 아래에서 여기 코드를 바꿉니다 -->
      <Modal  theme=""  @close="toggleModal">
        <h2>UVC</h2>
        <p>Learing font-end-developer course</p>
        <template v-slot:links>   
          <a href="#">아이디 찾기</a> 
          <a href="#">비번 찾기</a>
        </template>
      </Modal>
    </div>
    <!--  -->
    <div v-if="showModalTwo">
      <Modal @close="toggleModalTwo">
        <h1>Sign up to the newsletter</h1>
        <p>For updates and promotion code!</p>
      </Modal>
    </div>

    <button @click="toggleModal">open modal 1</button>
    <button @click="toggleModalTwo">open modal 2</button>
</template>

```  
일단, 이렇게 내용을 적는다.  그리고,  
```   <teleport to=".modals"   v-if="showModal"  > ``` 로 변경한다.  
여기서 ' to="css셀렉터" '는 teleport가 어디에 있는지 알려주는 것인데 css셀렉터를 전달해야 하기 때문에 <b>.modals </b>라고 적어야 한다.
[App.vue]의 나머지 내용도 추가하자. 

```html
<script>
import Modal from './components/Modal.vue'
export default {
  name :'App',
  components :{ Modal}, 
  data(){
    return {
      title :"My First Vue Application",
      comments:"회원가입 | 로그인",
      text:'가입혜택이 있습니다',
      showModal:false,
      showModalTwo:false
    }
  },
  methods:{
    toggleModal(){
      this.showModal = !this.showModal
    },
    toggleModalTwo(){
      this.showModal = !this.showModal
    }
  }
}
</script>

```

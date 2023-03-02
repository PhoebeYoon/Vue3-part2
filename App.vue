<template>
  <h1>{{ title }}</h1>
  <p>created by Vue3</p>
    <div v-if="showModal"  >
      <Modal :comments="comments" :text ="text" theme="sale"  @close="toggleWin"/>
    </div>
    <button @click="toggleWin">팝업창보기</button>
</template>
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
      showModal:false
    }
  },
  methods:{
    toggleWin(){
      this.showModal = !this.showModal
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

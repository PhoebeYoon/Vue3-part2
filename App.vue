<template>
  <h1>{{ title }}</h1>
  <p>created by Vue3</p>
    <div v-if="showModal"  >
      <Modal  theme="sale"  @close="toggleWin">
        <!-- <h2>UVC</h2>
        <p>Learing font-end-developer course</p> -->
        <h2>UVC</h2>
        <p>Learing font-end-developer course</p>

        <template v-slot:links>   
          <a href="#">아이디 찾기</a> 
          <a href="#">비번 찾기</a>
        </template>

      </Modal>
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

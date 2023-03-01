<template>
  <h1>{{  title  }}</h1>
  <input type="text" ref="inputbox">
  <button @click="handleClick">Click me</button>
  <button @click="takeValue">입력한값 출력하기</button>

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
      this.$refs.inputbox.classList.add('active')
      this.$refs.inputbox.focus()
    },
    takeValue(){
      console.log(this.$refs.inputbox.value)
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
h1 { border-bottom: 2px dashed #000; 
  padding-bottom:10px;}
</style>

<template>
  <form @submit.prevent="handleSubmit">
    <label>Email : </label>
    <input type="email" required v-model="email">
    <label>password : </label>
    <input type="password" required v-model="pw">
    <div v-if="passwordErr"  class="error">{{ passwordErr }}</div>
   <label> Role:</label>
   <select v-model="role">
    <option value="developer">Web Developer</option>
    <option value="designer">Web Designer</option>
   </select>
   <label>Skills :</label>
   <input type="text" v-model="tempSkill" @keydown.enter="addSkill">
   <div  v-for="skill in skills" :key="skill" class="pill">
    <span @click="deleteSkill(skill)"> {{ skill }} </span>
  </div>
   <div class="term" >
    <input type="checkbox" v-model='terms' required>
    <label>Terms and Conditions</label>
   </div>
   <div class="submit">
    <button>Create an account</button>
   </div>
  </form>
  <!-- <p>{{  email }} , {{ pw }}, {{ role }} , {{ terms}} , {{ skills }}</p>  -->
</template>
<script>
export default {
data() {
  return {
    email: '',
    pw:'',
    role :'',
    terms:false,
    skills:[],
    passwordErr: ''
  }
},
methods: {
  addSkill(e){
    if(this.tempSkill ) {  
      if ( !this.skills.includes(this.tempSkill)){
        this.skills= this.skills.concat(this.tempSkill.split(","))
      }
  }},
  deleteSkill(skill){
    //console.log(skill)
    this.skills= this.skills.filter((value)=>{ return value !==skill })
  },
  handleSubmit(){
      this.passwordErr= this.pw.length >=5 ? "" : '비밀번호는 최소6자이상 입력하세요'
  }
}
}
</script>
<style>
form {
  max-width: 420px; margin: 30px auto;
  background: white; text-align: left;
  padding: 40px; border-radius: 10px;
}
label {
  color: #aaa; display: inline-block;
  margin: 25px 0 15px; font-size: 0.6em;
  text-transform: uppercase; letter-spacing: 1px;
  font-weight: bold;
}
input, select {
  display: block; padding: 10px 6px;
  width: 100%; box-sizing: border-box;
  border: none; color: #555;
  border-bottom: 1px solid #ddd;
}
input[type="checkbox"]{
  display: inline-block; margin:0 10px 0 0;
  position: relative;top : 2px;
  width: 16px; 
}
.pill { display: inline-block; margin:20px 10px 0 0 ;
  padding:6px 12px; background: #eee; border-radius: 20px;
  font-size: 12px; letter-spacing: 1px;
  font-weight: bold; color:#777; cursor: pointer;}
button { background: #0b6dff; border: 0; padding:10px 20px;
  margin-top: 20px; color:#fff; border-radius: 20px;}
.submit { text-align: center;}
.error { color:crimson; margin-top: 10px; 
  font-size: 0.8em; font-weight: bold;
}
</style>
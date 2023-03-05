##### :cactus: Vue3 -part2

#### 이제 마무리를 해 봅시다. 

추가한 내용은  
1. submit 버튼를 가장아래에 추가하고
2. 비밀번호를 최소6자이상인지 검사하고, 6자이하라면 에러메시지를 출력해 하도록 했습니다.
3. 이것을 위해 form태그에 @submit.prevent를 추가했는데 submit될때 비밀번호의 입력자리수를 검사할 것입니다.

코드는 아래와 같습니다.   
```html
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
```   
data에 passwordErr 항목을 추가했고, methods에 handleSubmit함수를 추가했습니다.  
기존의 스타일에 아래 내용을 추가합니다. 

``` style
button { background: #0b6dff; border: 0; padding:10px 20px;
  margin-top: 20px; color:#fff; border-radius: 20px;}
.submit { text-align: center;}
.error { color:crimson; margin-top: 10px; 
  font-size: 0.8em; font-weight: bold;
}
```

##### :cactus: Vue3 -part2

##### 이전내용을 이어서 진행합니다.
input의 텍스트 상자에 skills 항목을 적어서 넣는 것을 해 보겠습니다.  

```html
<template>
  <form>
    <label>Email : </label>
    <input type="email" required v-model="email">
    <label>password : </label>
    <input type="password" required v-model="pw">
   <label> Role:</label>
   <select v-model="role">
    <option value="developer">Web Developer</option>
    <option value="designer">Web Designer</option>
   </select>
   <label>Skills :</label>
   <input type="text" v-model="tempSkill" @keyup="addSkill">
   <div class="term" >
    <input type="checkbox" v-model='terms' required>
    <label>Terms and Conditions</label>
   </div>
  </form>
  <p>{{  email }} , {{ pw }}, {{ role }} , {{ terms}} , {{ skills }}</p> 
</template>
<script>
export default {
data() {
  return {
    email: '',
    pw:'',
    role :'',
    terms:false,
    skills:[]  // 여러개의 항목
  }
},
methods: {
  addSkill(e){

    if(e.keyCode =="13" && this.tempSkill ) {   // 엔터키는 keyCode가 13입니다
      if ( !this.skills.includes(this.tempSkill)){  // 이미 skills배열에 새로운내용이 포함되어있지 않다면
        this.skills= this.skills.concat(this.tempSkill.split(",")) // 새로 입력한 내용이 여러개일경우 구분
      }
      this.tempSkill=''
    }
  }
}
}
</script>

```   
1) 여기서 skills은  항목을 여러개 적을 수 있기 때문에 배열로 선언했고,  
2) "html, css, js 등등" 으로 적고 입력 끝의 의미로 엔터를 입력한다는 가정하에 e.keyCode ==13(엔터)를 조건문으로 넣었습니다.  
3) 그리고 입력했던 내용을 또 입력하는 것을 방지하기 위해 skills 배열에 새로 입력한 내용이 이미 있는지 확인하기 위해 includes() 함수를 사용했습니다.   
4) 겹치는 내용이 없다면 ","로 입력한 내용을 구별하고 (split(",")
5) 그것을 기존의 내용과 합치도록 했습니다 (concat() 함수)



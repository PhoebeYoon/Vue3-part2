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
4) 겹치는 내용이 없다면 ","로 입력한 내용을 구별하고 (split(","))
5) 그것을 기존의 내용과 합치도록 했습니다 (concat() 함수)  

여기까지 잘 따라왔다면 스타일을 조금 추가한 후에 이번에는 입력했던 skills 중에 선택적으로 삭제하는 것을 추가해 보도록 하겠습니다.
p태그에 나열되었던 skill를   
```
 <div  v-for="skill in skills" :key="skill" class="pill">
```   
이것으로 대치합니다. 그리고 methods 항목에 아래 내용을 추가합니다.  
```
 deleteSkill(skill){
    //console.log(skill)
    this.skills= this.skills.filter((value)=>{ return value !==skill })
  }
```  
skills 중 원하는 항목을 클릭하면 그 항목을 매개변수로 전달하여 해당 항목을 삭제하는 것입니다.  
마지막으로 스타일에 아래 내용을 추가합니다.   
```
.pill { display: inline-block; margin:20px 10px 0 0 ;
  padding:6px 12px; background: #eee; border-radius: 20px;
  font-size: 12px; letter-spacing: 1px;
  font-weight: bold; color:#777; cursor: pointer;}
  ```   
<img width="276" alt="스크린샷 2023-03-05 오전 12 14 15" src="https://user-images.githubusercontent.com/48478079/222913996-af51947a-6e05-4b3c-90d6-cb735407ef8f.png">

이렇게 html,css,js를 입력했다면 이 3개 중 하나를 클릭하면 해당 항목이 삭제가 됩니다. 여기까지 잘 따라오셨습니다. 수고하셨습니다.



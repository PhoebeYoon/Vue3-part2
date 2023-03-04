##### :cactus: Vue3 -part2

#### 이전 수업내용에 이어서 진행됩니다.

[SignUp.vue] 파일에 변경합니다.
```html
<template>
  <form>
    <label>Email : </label>
    <input type="email" required v-model="email">
    <label>password : </label>
    <input type="password" required v-model="pw">
    <select v-model="role">
      <option value="developer">Web Developer</option>
      <option value="designer">Web Designer</option>
   </select>
  <div class="term" >
    <input type="checkbox" v-model='terms' required>
    <label>Terms and Conditions</label>
   </div>
   
  </form>
  <p>{{  email }} , {{ pw }}, {{ role }},{{ terms}} </p> <!-- 이것은 입력한 내용을 확인 -->
</template>
<script>
export default {
data() {
  return {
    email: '',
    pw:'',
    role :'',
    terms:false
  }
}
}
</script>
<style>
/* 기존스타일시트에 추가  */
input[type="checkbox"]{
  display: inline-block; margin:0 10px 0 0;
  position: relative;top : 2px;
  width: 16px; 
}
</style>

```   
여기서 return문의 email 내용을 변경하고, pw의 내용을 변경하면 출력화면에서 바뀐내용으로 나옵니다. 그 얘기는 input태그에 어떤 내용을 사용자가 입력하면 data문의 email 변수에 그대로 반영된다는 의미입니다. (이미 수업에서 다루었던 것입니다 )

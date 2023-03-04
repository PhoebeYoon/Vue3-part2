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

이제 내용을 더 추가하여 체크박스를 선택하면 해당 value의 값을 얻어오는 것을 해보자.  
```html
<!-- 폼태그안에 추가 -->
<div>
    <input type="checkbox" v-model="names" value="kim">
    <label for="">kim</label>
</div>
<div>
    <input type="checkbox" v-model="names" value="park">
    <label for="">park</label>
</div>
<div>
    <input type="checkbox" v-model="names" value="yoon">
    <label for="">Yoon</label>
</div>

```  

위의 내용을 보면 v-model="names"로 모두 같은 값을 갖고 있다. 그래서  
```javascript
// return 에 추가
names:[]
```
여기까지 완성하고 브라우저에서 확인을 해보면 아래 이미지와 같을 것이다.   

<img width="354" alt="스크린샷 2023-03-04 오후 5 55 53" src="https://user-images.githubusercontent.com/48478079/222886730-a6c6b789-b9a0-4e4c-8751-57fc14199519.png">







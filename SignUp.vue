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
   <div class="term" >
    <input type="checkbox" v-model='terms' required>
    <label>Terms and Conditions</label>
   </div>

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

  </form>
  <p>{{  email }} , {{ pw }}, {{ role }} , {{ terms}} , {{ names }}</p> 
</template>

<script>
export default {
data() {
  return {
    email: '',
    pw:'',
    role :'',
    terms:false,
    names:[]
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


</style>
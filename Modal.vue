<template>
  <div class="backdrop"> 
    <div class="modal">
      <p> Modal content</p>
    </div>
  </div>
</template>
<style scoped>
.modal {
  width:400px; padding:20px; margin:30% auto;
  background: white;
  border-radius: 10px;
}
p { color:hotpink; font-size: 120%; }
.backdrop{ top:0; position: fixed;
  background: rgba(0,0,0,0.5);
  width: 100%;  height: 100%;}
</style>
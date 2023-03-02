<template>
  <div class="backdrop"> 
    <div class="modal" :class="{sale: theme =='sale'}">
      <h2>{{ comments}}</h2>
      <p> Modal content</p>
      <span> {{ text }}</span>
    </div>
  </div>
</template>

<script>
export default {
  props:[ 'comments','text', 'theme']
}
</script>
<style scoped>
.modal {
  width:400px; padding:20px; margin:30% auto;
  background: white;
  border-radius: 10px;
}
.modal p { color:hotpink; font-size: 120%; }
.backdrop{ top:0; position: fixed;
  background: rgba(0,0,0,0.5);
  width: 100%;  height: 100%;}
.modal.sale { background:crimson; color:#fff }
.modal.sale h1 { color: #fff;}
/*  */
</style>
<template>
  <div class="backdrop" @click.self="closeModal"> 
    <div class="modal" :class="{sale: theme =='sale'}">
      <slot>이내용은 부모에서 디폴트slot에 들어갈 내용이 사라질때만 보입니다</slot>
      <!--부모에서 디폴트 <slot>에 들어갈 내용이 사라질때만 보입니다  -->
      <div class="actions">
        <slot name="links"></slot>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props:['theme'],
  methods:{ closeModal(){ 
      //alert('ok')
      this.$emit('close')
  }}
}
</script>
<style>
.modal {
  width:400px; padding:20px; margin:30% auto;
  background: white;
  border-radius: 10px;
}
.modal p { color:#fff; font-size: 120%; }
.backdrop{ top:0; position: fixed;
  background: rgba(0,0,0,0.5);
  width: 100%;  height: 100%;}
.modal.sale { background:crimson; color:#fff }
.modal.sale h1 { color: #fff;}
.modal .actions{
  text-align: center; margin:30px 0 10px 10px;
}
.modal .actions a{ color:#333; padding: 8px; 
  border:1px solid #eee; border-radius: 4px; 
  text-decoration: none; margin: 10px;}
.modal.sale .actions a{
  color:white
}
</style>
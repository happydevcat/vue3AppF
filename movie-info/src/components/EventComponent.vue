<template>
  <div class="event" :class="{show: isOpen}">
    <p>{{text}}</p>
    <button @click="isOpen=false">X</button>
  </div>
</template>

<script>
export default {
  name: 'EventComponet',
  props:{
    text:String,
  },
  data(){
    return{
      isOpen : true
    }
  }
}
</script>

<style  scoped>
  .event {
    background: #444;
    padding: 10px 20px;
    color: #fff;
    display: flex;
    justify-content: space-between;
    align-items: center;
    display: none;
  }

  .show{
    display: flex;
  }
  .event button{
    margin:0;
  }
</style>
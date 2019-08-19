<template>
  <div id="app" :style="containerStyle">
    <router-view/>
  </div>
</template>
<script>
export default {
  name: 'App',
  data(){
    return{
      containerStyle:{
        height:0,
        width:0,
      }
    }
  },
  created(){
    window.addEventListener('resize', this.getContainerSize);
    this.getContainerSize();
  },
  methods:{
    getContainerSize(){
      this.containerStyle.height = document.body.clientHeight + 'px';
      this.containerStyle.width = document.body.clientWidth + 'px';
    },
  }
}
</script>

<style>
  html,body{
    margin: 0;
    padding: 0;
    font-size: 16px;
  }
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>

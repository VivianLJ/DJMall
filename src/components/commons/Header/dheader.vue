<style>
  @import './dheader.css';
  .d-header{
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    min-width: 1024px;
    height: 64px;
    line-height: 78px;
    text-align: left;
    background: transparent;
    /*border-bottom: 1px solid #efefef;*/
    display:flex;
    align-items: center;
    flex-wrap: nowrap;
    justify-content: center;
    -webkit-transition: all .3s ease;
    transition: all .3s ease;
    z-index: 9999;
  }
  .d-header > img{
    margin: 0 38px;
  }
  .d-h-container{
    align-items: center;
    -webkit-box-flex: 1;
    -moz-flex: 1;
    flex: 1;
    display: -webkit-box;
    display: flex;
    -webkit-box-pack: justify;
    -moz-justify-content: space-between;
    justify-content: space-between;
  }
  .d-header:hover{
    background: #ffffff;
  }
  .d-h-menu{
    height: 100%;
    margin-right: 24px;
  }
  .d-h-menu > ul{
    height: 100%;
    list-style: none;
  }
  .d-h-menu > ul > li{
    float: left;
    text-decoration: none;
    /*padding: 0 12px;*/
    font-size: 0.88rem;
    font-weight: 600;
    cursor: pointer;
    height: 64px;
    line-height: 64px;
  }
  .d-h-menu > ul > li:hover{
    height: 62px;
    border-bottom: 2px solid #2c3e50;
  }
  .d-h-menu > ul > li:not(:last-child){
   margin-right: 24px;
  }
  .d-h-funcarea{
    margin-right: 12px;
    height: 100%;
    line-height: 64px;
    display: flex;
    align-items:center;
  }
  .d-h-funcarea > img{
    width: 24px;
    margin: 0 10px;
    cursor: pointer;
  }
  .d-h-f-button{
    height: 50%;
    color: #ffffff;
    border-radius: 4px;
    margin-right: 24px;
    background-image: -webkit-gradient(linear,left top, left bottom,from(#42b7ff),to(#1897f2));
    background-image: linear-gradient(-180deg,#42b7ff,#1897f2);
    padding: 6px 12px;
    border: none;
    cursor: pointer;
    font-weight: 600;
    outline: none;
    min-width: 50px;
  }
  .d-h-f-button:hover{
    background-image: -webkit-gradient(linear,left top, left bottom,from(#42b7ff),to(#29aeff));
    background-image: linear-gradient(-180deg,#42b7ff,#29aeff);
  }
</style>
<template>
  <div class="d-header" @mouseenter="mouseEnter" @mouseleave="mouseLeave">
    <img :src="logoImg" alt="">
    <div class="d-h-container">
      <div class="d-h-menu">
        <ul>
          <li :style="{color : liColor}" v-for="(item,index) in menu" :key="index">{{item}}</li>
        </ul>
        <slot name="menu-item"></slot>
      </div>
      <div class="d-h-funcarea">
        <slot name="function-area">
          <button class="d-h-f-button">商城</button>
          <img :src="iconSearch" alt="">
          <img :src="iconUser" alt="">
        </slot>
      </div>
    </div>
  </div>
</template>
<script>
  export default{
    name:'header',
    props:{
      menu:Array,
    },
    data(){
      return{
        // menu:['消费级产品','专业级产品','行业应用','系统模块','探索精彩','服务与支持'],
        liColor:'#ffffff',
        logoImg:'https://www1.djicdn.com/assets/images/v3/logo-white-b41f40998f5c6b07e90e184fb34ed4bc.svg',
        iconSearch:'https://www2.djicdn.com/assets/images/v3/head/search-white-706c958a64f9227a75416080c1884afd.svg',
        iconUser:'https://www4.djicdn.com/assets/images/v3/head/user-white-cc54de17d02296a04cdb1bb25be67e21.svg',
      }
    },
    methods:{
      mouseEnter(){
        this.liColor = '#303233';
        this.logoImg = 'https://www2.djicdn.com/assets/images/v3/logo-black2-145dcb13c56f36a65d084180a42136fa.svg';
        this.iconSearch = 'https://www3.djicdn.com/assets/images/v3/head/search2-f59385661d469676263d42217b56605a.svg';
        this.iconUser = 'https://www1.djicdn.com/assets/images/v3/head/user-ab280f4807cc9843ed51d34f78e7c960.svg';
      },
      mouseLeave(){
        this.liColor = '#ffffff';
        this.logoImg = 'https://www1.djicdn.com/assets/images/v3/logo-white-b41f40998f5c6b07e90e184fb34ed4bc.svg';
        this.iconSearch = 'https://www2.djicdn.com/assets/images/v3/head/search-white-706c958a64f9227a75416080c1884afd.svg';
        this.iconUser = 'https://www4.djicdn.com/assets/images/v3/head/user-white-cc54de17d02296a04cdb1bb25be67e21.svg';
      },
    }
  }
</script>

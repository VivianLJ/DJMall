<style>
.d-content{
  width: 100%;
  height: 55%;
  background: #404040;
  position: absolute;
  left: 0;
  top: 0;
  z-index: 99;
  padding-top: 74px;
}
</style>
<template>
  <div style="height: 100%;width: 100%;">
    <DHeader :menu="menu">
      <div slot="menu-item">
        <div ref="menuitem1" style="width: 100%;height: 20%;background: #ffec5e;position: absolute;top: 64px;left: 0;display: none;">
        </div>
        <div ref="menuitem2" style="width: 100%;height: 20%;background: #b6ff59;position: absolute;top: 64px;left: 0;display: none;">
        </div>
        <div ref="menuitem3" style="width: 100%;height: 20%;background: #ffaf5e;position: absolute;top: 64px;left: 0;display: none;">
        </div>
        <div ref="menuitem4" style="width: 100%;height: 20%;background: #ffec5e;position: absolute;top: 64px;left: 0;display: none;">
        </div>
        <div ref="menuitem5" style="width: 100%;height: 20%;background: #b6ff59;position: absolute;top: 64px;left: 0;display: none;">
        </div>
        <div ref="menuitem6" style="width: 100%;height: 20%;background: #ffaf5e;position: absolute;top: 64px;left: 0;display: none;">
        </div>
      </div>
    </DHeader>
    <div class="d-content">
      <swiper :options="swiperOption">
        <swiper-slide v-for="(slide, index) in swiperSlides" :key="index">I'm Slide {{ slide }}</swiper-slide>
        <div class="swiper-pagination" slot="pagination"></div>
      </swiper>
    </div>
  </div>
</template>
<script>
  import DHeader from './commons/Header/dheader.vue'
  export default{
    name:'mainPage',
    components:{
      DHeader:DHeader
    },
    data(){
      return{
        menu:['消费级产品','专业级产品','行业应用','系统模块','探索精彩','服务与支持'],
        swiperOption: {
          // some swiper options/callbacks
          // 所有的参数同 swiper 官方 api 参数
          // ...
          pagination: {
            el: '.swiper-pagination'
          }
        },
        swiperSlides: [1, 2, 3, 4, 5]
      }
    },
    mounted() {
      setInterval(() => {
        console.log('simulate async data');
        if (this.swiperSlides.length < 10) {
          this.swiperSlides.push(this.swiperSlides.length + 1)
        }
      }, 3000)
    }
  }
</script>

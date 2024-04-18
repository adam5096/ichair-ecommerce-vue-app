<template>
  <swiper 
  :slides-per-view="3" 
  :space-between="30" 
  :navigation="true" 
  :modules="modules" 
  class="mySwiper">
    <swiper-slide v-for="(item) in items.slice(0, 5)" :key="item.id">
      <img :src="item.imgUrl" alt="" @click="bannerChange(item.id)">
    </swiper-slide>
  </swiper>
</template>

<script setup>
// 匯入swiper核心模組
import { Navigation } from "swiper/modules";
// 匯入swiper 的vue元件
import { Swiper, SwiperSlide } from "swiper/vue";
// 匯入swiper樣式
import 'swiper/css'
import 'swiper/css/navigation'

// 取出元件實例並命名components以利操作
const components = {
  Swiper, SwiperSlide
}
// 取出元件實例並命名modules以利操作
const modules = [Navigation]

// 聲明並註冊接收來自父元件Banner傳遞的屬性與值
const props = defineProps({
  items: {
    type: Array,
    required: true
  },
  bannerChange: {
    type: Function,
    required: true
  }
})
</script>

<style>
.swiper {
  /* background-color: chocolate; */
  position: absolute;
  bottom: 50px;
  left: 10%;
  width: 30%;
  padding-top: 10px;
  padding-bottom: 50px;
}

.swiper-slide {
  background-position: center;
  background-size: cover;
  width: 100px;
  height: 100px;
  cursor: pointer;
}

.swiper .swiper-button-prev {
  position: absolute;
  left: 0;
  top: 50%;
  width: 54px;
  height: 54px;
}

.swiper .swiper-button-next {
  position: absolute;
  right: 0;
  top: 50%;
  width: 54px;
  height: 54px;
}

.swiper .swiper-button-next::after,
.swiper .swiper-button-prev::after {
  font-size: 30px;
  line-height: 0;
  width: 54px;
  height: 54px;
  background: transparent;
  border-radius: 50%;
  transition: 0.3s;
  color: rgba(255, 255, 255, 1);
  border: 1px solid rgba(255, 255, 255, 0.5);
  /* 毛玻璃效果 */
  backdrop-filter: blur(20px);
  display: flex;
  align-items: center;
  justify-content: center;
}

.swiper .swiper-button-next:hover,
.swiper .swiper-button-prev:hover {
  border-radius: 50%;
  background: rgba(255, 255, 255, 0.3) !important;
  color: rgba(255, 255, 255, 0.8) !important;
}

.swiper-slide img{
  display: block;
  width: 100%;
}


@media (max-width:1440px) {
  .swiper{
    position: absolute;
    bottom: 80px;
    left: 13%;
    width: 30%;
    padding-top: 10px;
    padding-bottom: 30px;
  }
}
</style>
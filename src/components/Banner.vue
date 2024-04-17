<template>
  <div class="banner">
    <BannerSlide v-for="item in items" :key="item.id" :item="item" />
    <BannerSwiper :items="items" :bannerChange="handleBannerChange" />
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import BannerSlide from './BannerSlide.vue'
import BannerSwiper from './BannerSwiper.vue'
const items = ref([])
// vue生命週期函數，在渲染樣板後第一時間執行本函數
onMounted(() => {
  // js ES5 fetch方法發送請求給json-server
  fetch('http://localhost:4000/items')
    .then(res => res.json())
    .then(data => items.value = data)
    .catch(e=>console.log(e.message))
});

// 在父元件Banner內自定義事件函數與callback函數，交由子元件BannerSwipe去觸發事件
// 1:38:12
const handleBannerChange = (id) => {
  items.value.map(item => {
    item.active = false
    if (item.id === id) item.active = true
    return item
    })
}
</script>

<style scoped>
.banner{
  position: relative;
  width: 100%;
  min-height: 90vh;
  background: var(--bgColor);
  transition: 1s;
}
@media (max-width:768px){
  .banner{
    min-height: 100vh;
  }
}
</style>
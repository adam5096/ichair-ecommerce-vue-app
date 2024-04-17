<template>
  <SideBar />
  <Header />
  <main id="main">
    <!-- 向路由註冊表router/index.js開啟對話 -->
    <!-- 你有幾條路由規則? 哪些元件是要渲染的路由元件?-->
    <router-view></router-view>
  </main>
</template>

<script setup>
import Header from '@/components/Header.vue'
import SideBar from '@/components/SideBar.vue'
</script>

<style scoped>

</style>

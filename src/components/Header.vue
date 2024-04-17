<template>
    <header id="home">
        <!-- 頂部導航 -->
        <router-link to="/" class="logo">iChairs</router-link>
        <ul class="nav">
            <li v-for="nav in navs" :key="nav.id">
                <router-link to="/" v-if="nav.name === 'Home'" :class="{ active: nav.active }"
                    @click="handleNavActive(nav.id)">
                    <i class="bi bi-house-door-fill"></i>
                </router-link>
                <router-link v-else to="/" :class="{ active: nav.active }" @click="handleNavActive(nav.id)">
                    {{ nav.name }}</router-link>
            </li>
        </ul>
        <!-- 功能區 -->
        <div class="features">
            <CartBtn />
        </div>
    </header>
</template>
<script setup>
import { navsData } from '@/data/data.js';
import CartBtn from './CartBtn.vue';
import { ref } from 'vue';

// 將源資料navsData內容填充給工作資料navs並使其建立響應式特性
// 將源資料與工作資料分割，避免修改到源資料，我們將操作都侷限在工作資料上
const navs = ref(navsData)
// 導航區中被點擊到的超連結要變色，其他連結維持原色
const handleNavActive = (id) => {
    // 拿到被點擊導航項的id去跟工作資料navs內的每個子項操作
    navs.value.map(nav => {//行為初始化先建立暫時物件nav，用來盛裝navs中的每個子資料集
        nav.active = false//先把全部子資料的nav.active屬性值改為false
        if (nav.id === id) nav.active = true//第二時間，針對被點擊到的導航項，將其nav.active再改為true
        return nav//回傳操作完畢後的工作內容
    })
}
</script>
<style scoped>
header {
    position: relative;
    width: 95%;
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 30px 100px 30px 200px;
    z-index: 1100;
}

.logo {
    font-size: 35px;
    color: #fff;
    letter-spacing: 2px;
    font-weight: 800;
}

.nav {
    display: flex;
}

.nav li {
    list-style: none;
    margin: 0 10px;
}

.nav li a {
    color: #fff;
    text-decoration: none;
    font-weight: 600;
    letter-spacing: 2px;
    cursor: pointer;
    transition: 0.3s;
}

.nav li:hover a,
.nav li a.active {
    color: var(--primary);
}

.features {
    display: flex;
    align-items: center;
    gap: 10px;
}

@media (max-width:768px) {
    header {
        padding: 10px 50px;
    }

    .nav {
        display: none;
    }
}
</style>
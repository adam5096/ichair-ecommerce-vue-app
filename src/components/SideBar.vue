<template>
    <div class="sideBar">
        <!-- .stop.prevent將點擊a標籤後的刷新+跳頁(瀏覽器行為)關閉 -->
        <!-- vue語法為DOM動態新增與移除樣式:class="{ active: active }" -->
        <a class="menu" :class="{ active: active }" @click.stop.prevent="handleToggleMenu">
            <i class="bi bi-menu-app-fill"></i></a>
        <ul class="sci">
            <li v-for="(sci) in scis" :key="sci.id">
                <a href="#"><i :class="sci.icon"></i></a>
            </li>
        </ul>
    </div>
    <SideMenu :active="active" />
</template>

<script setup>
import SideMenu from './SideMenu.vue'
import { ref } from 'vue'
const scis = [
    { id: 1, icon: 'bi bi-meta' },
    { id: 2, icon: 'bi bi-twitter-x' },
    { id: 3, icon: 'bi bi-instagram' },
]

const active = ref(false)
// 點擊選單發生動態樣式改變
const handleToggleMenu = () => {
    active.value = !active.value
}
</script>

<style scoped>
.sideBar {
    position: fixed;
    width: 5%;
    min-height: 100vh;
    padding: 30px;
    background: var(--primary);
    display: flex;
    justify-content: space-between;
    align-items: center;
    flex-direction: column;
    transition: 1s;
    z-index: 2000;
}

.menu {
    font-size: 1.6rem;
    color: #000;
    z-index: 2000;
    transition: ease 1s;
}

/* 側邊欄選單icon動態樣式 */
.menu.active{
    transform: rotateZ(180deg);
}

.sci{
    padding: 0;
    display: inline-flex;
    justify-content: flex-start;
    align-items: center;
    flex-direction: column;
    gap: 25px;
}

.sci li{
    list-style: none;
}

.sci li a{
    font-size: 1.6rem;
    color: #000;
}
</style>
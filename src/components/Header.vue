<template>
    <header id="home">
        <!-- 頂部導航 -->
        <router-link to="/" class="logo">iChairs</router-link>
        <Nav />
        <!-- 功能區 -->
        <div class="features">
            <!-- 購物車 -->
            <CartBtn />
        </div>
    </header>
</template>
<script setup>
import Nav from './Nav.vue'
import CartBtn from './CartBtn.vue';
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
<template>
    <div class="cart-btn">
        <router-link to="/cart" class="cart"><i class="bi bi-cart2"></i></router-link>
        <span class="count">???</span>
    </div>
</template>

<script setup>

</script>
<style scoped>
.cart-btn {
    display: flex;
    align-items: center;
    gap: 10px;
    transition: 0.5s;
}

.cart {
    font-size: 30px;
    color: #ffffff;
}

.count {
    font-size: 1.2rem;
    color: #ffffff;
    width: 30px;
    height: 30px;
    padding: 5px;
    border-radius: 50%;
    background: #00a950;
    display: flex;
    justify-content: center;
    align-items: center;
}
</style>
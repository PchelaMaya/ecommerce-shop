<template>
    <div class="hero">
        <Heroinformation
        title="Luxury homeware for people who love timeless design quality"
        description="Shop the new Spring 2022 collection today"
        link="#"
        colorLink="lightgray"
        />
    </div>
</template>

<script setup>
import Heroinformation from '@/components/Heroinformation.vue';
</script>

<style lang="scss" scoped>
.hero {
    background: url(/img/hero.jpg);
    height: 704px;
    background-size: cover;
    display: flex;
    align-items: center;
    justify-content: flex-end;
    padding-right: 80px;
}
</style>
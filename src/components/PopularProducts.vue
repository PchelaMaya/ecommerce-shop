<template>
    <Loader v-if="loading"/>
    <Products :products="popularProducts" v-else />

</template>

<script setup>
import { onMounted, ref } from 'vue'
import Loader from '@/components/UI/Loader.vue'
import Products from "@/components/Products4Column.vue"
import api from '@/api'

const popularProducts = ref([]);
const loading = ref(true);

onMounted(async () => {
    popularProducts.value = await api.getPopularProducts();
    loading.value = false;
});

</script>


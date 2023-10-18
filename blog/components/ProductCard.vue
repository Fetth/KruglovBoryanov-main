<template>
<div v-for="product in products" :key="id">
    <v-card :elevation="13" outlined>
        <v-img :src="product.image" height="180px"></v-img>
        <v-card-title>{{ product.title }}</v-card-title>
        <v-card-subtitle>{{ product.price }} руб.</v-card-subtitle>
        <v-card-actions>
            <v-btn variant="flat" color="indigo" @click="basketStore.add(this.product)">
                Купить
            </v-btn>
        </v-card-actions>
    </v-card>
</div>
</template>

<script setup>
const { product } = defineProps(['product'])


let products = ref([])

const data = await fetch('http://127.0.0.1:8000/api/v1/')
products = await data.json()
</script>

<style scoped>

</style>
<template>

<div v-for="product in products" :key="id" class="container">
    <v-card
    :loading="loading"
    class="mx-auto my-12"
    max-width="374"
  >
    <template slot="progress">
      <v-progress-linear
        color="deep-purple"
        height="10"
        indeterminate
      ></v-progress-linear>
    </template>

    <v-img :src="product.image" height="180px"></v-img>

    <v-card-title>{{ product.title }}</v-card-title>

    <v-card-text>{{ product.made }}</v-card-text>
    <v-card-subtitle>{{ product.price }} руб.</v-card-subtitle>

    <v-divider class="mx-4"></v-divider>
    <v-card-actions>
            <v-btn variant="flat" color="indigo" @click="basketStore.add(this.product)">
                Купить
            </v-btn>
        </v-card-actions>
  </v-card>

</div>


</template>

<script setup>

let products = ref([])

const data = await fetch('http://127.0.0.1:8000/api/v1/')
products = await data.json()

</script>

<style>
main {
    display: flex;
    flex-wrap: wrap;
    margin-left: 20px;
}

</style>
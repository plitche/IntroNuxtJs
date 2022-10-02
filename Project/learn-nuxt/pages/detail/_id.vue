<template>
  <div>
    <h1>상세 페이지</h1>
    <div>
        {{ product }}
        <img :src="product.imageUrl" :alt="product.name" />>
        <p>name: {{ product.name }}</p>
        <p>price: {{ product.price }}</p>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import { fetchProductById } from '@/api/index'

export default {
    // created() {
    //     const id = this.$route.params.id;
    //     fetchProductById(id);
    // }

    async asyncData({ params }) {
        // const id = params.id;
        const response = await fetchProductById(params.id);
        const product = response.data
        return { product }
    }
}
</script>

<style>

</style>
<template>
  <div>
    <p>메인 페이지입니다.</p>
    <div>
      <ul>
        <li v-for="product in products" :key="product.id">
          <img :src="product.imageUrl" :alt="product.name" />
          <p>{{ product.name }}</p>
          <p>{{ product.price }}</p>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  async asyncData() {
    const response = await axios.get('https://3000/products')
    console.log(response)
    const products = response.data.map(item => {
      return {
        ...item,
      imageUrl: `${item.imageUrl}?random=${Math.random()}`
      }
    })
    return { products }
  },

  // data() {
  //   return {
  //     products: []
  //   }
  // },
  // async created() {
  //   const response = await axios.get('https://3000/products')
  //   console.log(response)
  //   this.products = response.data
  // }

}
</script>

<style>

</style>
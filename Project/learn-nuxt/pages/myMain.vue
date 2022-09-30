<template>
  <div>
    <p>메인 페이지입니다.</p>
    <ProductList></ProductList>
  </div>
</template>

<script>
import axios from 'axios';
import ProductList from '~/components/ProjectList.vue'

export default {
  components: {
    ProductList
  },
  async asyncData() {
    const response = await axios.get('https://3000/products')
    console.log(response)
    const products = response.data
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
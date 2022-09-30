<template>
  <div>
    <p>메인 페이지입니다.</p>
    <div>
      {{ products }}
    </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  async asyncData() {
    const response = await axios.get('https://3000/products')
    console.log(response)
    this.products = response.data
  },
  data() {
    return {
      products: []
    }
  },
  async created() {
    const response = await axios.get('https://3000/products')
    console.log(response)
    this.products = response.data
  }

}
</script>

<style>

</style>
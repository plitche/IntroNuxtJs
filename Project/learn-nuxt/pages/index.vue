<template>
  <div class="app">
    <main>
      <div>
        <input type="Text" />
      </div>
      <main>
        <ul>
          <li 
          class="item flex" 
          v-for="product in products" 
          :key="product.id" 
          @click="moveToDetailPage(product.id)">
            <img class="product-image" :src="product.imageUrl" :alt="product.name" />
            <p>{{ product.name }}</p>
            <span>{{ product.price }}</span>
          </li>
        </ul>
      </main>
    </main>
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

  methods: {
    moveToDetailPage(id) {
      console.log(id)
    },
  }
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

<style scoped>
.flex {
  display: flex;
  justify-content: center;
}
.item {
  display: inline-block;
  width: 400px;
  height: 300px;
  text-align: center;
  margin: 0 0.5rem;
  cursor: pointer;
}
.product-image {
  width: 400px;
  height: 250px;
}
.app {
  position: relative;
}
.cart-wrapper {
  position: sticky;
  float: right;
  bottom: 50px;
  right: 50px;
}
.cart-wrapper .btn {
  display: inline-block;
  height: 40px;
  font-size: 1rem;
  font-weight: 500;
}
</style>
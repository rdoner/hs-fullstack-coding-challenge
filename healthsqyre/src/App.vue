<template>
  <div>
    <button v-if=sortedByPrice @click="sortedByPrice = !sortedByPrice">Sort By Id</button>
    <button v-else @click="sortedByPrice = !sortedByPrice">Sort By Price</button>
    <!-- <button @click="sorting *= -1">Toggle order</button> -->
    <ul>
      <li v-for="item in sortedItems" :key="item.id">
        <h1>{{ item.id }}</h1>
        <h1>{{ item.name }}</h1>
        <h2>{{ item.vendor.name }}</h2>
        <h2>${{ item.price }}</h2>
        <h2 v-html="item.description"></h2>
      </li>
    </ul>
  </div>
</template>

<script>
import { DATA } from "../data.const";
export default {
  name: "App",
  // data() {
  //   // const sortedById = DATA.sort((a, b) => {
  //   //     return a.id - b.id;
  //   //   })
  //   // const sortedByPrice = DATA.sort((a, b) => {
  //   //     return a.price - b.price;
  //   //   })
  //   return {
  //     items: DATA
  //   };
  // },

  data: () => ({
    sortedByPrice: false
  }),
  computed: {
    sortedItems() {
      if (this.sortedByPrice) {
        return DATA.sort((a, b) => {
          return a.price - b.price;
        });
      } else {
        return DATA.sort((a, b) => {
          return a.id - b.id;
        })
      }
    }
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

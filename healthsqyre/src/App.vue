<template>
  <ul id="example-1">
    <li v-for="item in items" :key="item.id">
      <h1>{{ item.name }}</h1>
      <h2>{{ item.vendor.name }}</h2>
      <h2>${{ item.price }}</h2>
      <h2 v-html="description"></h2>
      <!-- <h2>{{{ item.description }}}</h2> -->
    </li>
  </ul>
</template>

<script>
import { DATA } from "../data.const";
export default {
  name: "App",
  data() {
    return {
      items: DATA
    };
  },
  computed: {
    description: function() {
      var str = "<div><p>some html</p></div>";
      return str;
    }
  }
  // components: {
  //   Catalog
  // }
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

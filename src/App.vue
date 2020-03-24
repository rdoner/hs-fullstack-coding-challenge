<template>
  <div>
    <header>
      <h1>HEALTHSQYRE</h1>
    </header>
    <main>
      <div class="sort-btn">
        <button v-if="sortedByPrice" @click="sortedByPrice = !sortedByPrice">Sort By Id</button>
        <button v-else @click="sortedByPrice = !sortedByPrice">Sort By Price</button>
      </div>
      <ul class="container">
        <li class="item" v-for="item in sortedItems" :key="item.id">
          <img src="./assets/cpap.jpg" alt="CPAP machine" />
          <div class="text">
            <h1>{{ item.name }}</h1>
            <p>{{ item.vendor.name }}</p>
            <p class="price">${{ item.price }}</p>
            <p class="desc" v-html="item.description"></p>
          </div>
        </li>
      </ul>
    </main>
  </div>
</template>

<script>
import { DATA } from "../data.const";
export default {
  name: "App",
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
        });
      }
    }
  }
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

header {
  height: 100px;
  background-color: rgb(0, 89, 96);
  display: flex;
  justify-content: center;
  align-items: center;
  font-family: "Sen", sans-serif;
  color: white;
}

.sort-btn {
  display: flex;
  justify-content: center;
  margin: 20px;
}

.container {
  display: flex;
  flex-flow: row wrap;
  height: auto;
  justify-content: space-evenly;
  list-style-type: none;
  padding: 0;
}

.item {
  box-sizing: border-box;
  margin: 1rem;
  text-align: center;
  box-shadow: 0 4px 10px 0 rgba(0, 0, 0, 0.2), 0 4px 20px 0 rgba(0, 0, 0, 0.19);
}

.text {
  padding: 2rem;
}

img {
  max-width: 100%;
  max-height: 100%;
}

@media only screen and (min-width: 480px) {
  .item {
    max-width: 100%;
  }
}

@media only screen and (min-width: 768px) {
  .item {
    max-width: 45%;
  }
}
@media only screen and (min-width: 1000px) {
  .item {
    max-width: 30%;
  }
}

.price {
  color: green;
}
.desc {
  text-align: left;
}
</style>

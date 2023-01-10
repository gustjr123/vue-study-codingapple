<template>
  <div class="menu">
    <a v-for="i in menus" :key="i"> {{ i }} </a>
  </div>

  <div v-for="value in products" :key="value.product">
    <h4 :style="style">{{ value.product }}</h4>
    <p>{{ value.price }} 만원</p>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      menus: ["Home", "Products", "About"],
      products: [
        { product: "역삼동원룸", price: 50 },
        { product: "천호동원룸", price: 60 },
        { product: "마포구원룸", price: 70 },
      ],
      style: "color: blue",
    };
  },
  components: {},
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.menu {
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}
.menu a {
  color: white;
  padding: 10px;
}
</style>

<template>
  <img alt="Vue logo" src="./assets/logo.png" />
  <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
  <h1 :style="titleStyle">원룸보여줌</h1>
  <div class="menu">
    <a v-for="(item, index) in menu" :key="item">{{ `${index}. ${item}` }}</a>
  </div>
  <div v-for="(product, index) in products" :key="product">
    <h4>{{ product }}</h4>
    <p>{{ prices[index] + " 만원" }}</p>
    <button @click="increase(index)">허위매물 신고</button>
    <span>신고수: {{ singo[index] }}</span>
  </div>
</template>

<script>
// import HelloWorld from "./components/HelloWorld.vue";

export default {
  name: "App",
  components: {
    // HelloWorld,
  },
  data() {
    return {
      titleStyle: "color: blue",
      products: ["역삼동원룸", "천호동원룸", "마포구원룸"],
      prices: [50, 60, 70],
      menu: ["Home", "Products", "About"],
      singo: [0, 0, 0],
    };
  },
  methods: {
    increase(index) {
      this.singo[index]++;
    },
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

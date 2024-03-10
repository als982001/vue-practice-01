<template>
  <img alt="Vue logo" src="./assets/logo.png" />
  <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
  <h1 :style="titleStyle">원룸보여줌</h1>
  <div>
    <h4>{{ products[0] }} 원룸</h4>
    <p>{{ price1 }} 만원</p>
  </div>
  <div>
    <h4>{{ products[1] }} 원룸</h4>
    <p>{{ price2 }} 만원</p>
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
      price1: 60,
      price2: 50,
      titleStyle: "color: blue",
      products: ["역삼동원룸", "천호동원룸", "마포구원룸"],
    };
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

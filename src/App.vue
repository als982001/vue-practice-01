<template>
  <div class="black-bg" v-if="showModal" @click="showModal = false">
    <div class="white-bg">
      <h4>상세페이지</h4>
      <p>상세페이지내용임</p>
      <button @click="showModal = false">닫기</button>
    </div>
  </div>
  <img alt="Vue logo" src="./assets/logo.png" />
  <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
  <h1 :style="titleStyle">원룸보여줌</h1>
  <div class="menu">
    <a v-for="(item, index) in menu" :key="item">{{ `${index}. ${item}` }}</a>
  </div>
  <div v-for="(product, index) in products" :key="product">
    <img src="./assets/room0.jpg" />
    <h4 @click="handleModal()">{{ product }}</h4>
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
      imgs: ["./assets/room0.jpg", "./assets/room1.jpg", "./assets/room2.jpg"],
      showModal: false,
    };
  },
  methods: {
    increase(index) {
      this.singo[index]++;
    },
    handleModal() {
      this.showModal = !this.showModal;
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

body {
  margin: 0;
}
div {
  box-sizing: border-box;
}
.black-bg {
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  position: fixed;
  padding: 20px;
}
.white-bg {
  width: 100%;
  background: white;
  border-radius: 8px;
  padding: 20px;
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

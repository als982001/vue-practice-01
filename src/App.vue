<template>
  <img alt="Vue logo" src="./assets/logo.png" />
  <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
  <InfoModal
    :onerooms="onerooms"
    :showModal="showModal"
    :clickedIndex="clickedIndex"
    :handleRemoveModal="handleRemoveModal"
  />
  <h1 :style="titleStyle">원룸보여줌</h1>
  <Discount />
  <div class="menu">
    <a v-for="(item, index) in menu" :key="item">{{ `${index}. ${item}` }}</a>
  </div>
  <div v-for="(oneroom, index) in onerooms" :key="oneroom.title">
    <ProductInfo
      :oneroom="oneroom"
      :handleShowModal="handleShowModal"
      :index="index"
    />
  </div>
</template>

<script>
// import HelloWorld from "./components/HelloWorld.vue";
import onerooms from "./assets/onerooms";
import DiscountComponent from "./components/DiscountComponent.vue";
import InfoModal from "./components/InfoModal.vue";
import ProductInfo from "./components/ProductInfo";

export default {
  name: "App",
  components: {
    // HelloWorld,
    Discount: DiscountComponent,
    InfoModal,
    ProductInfo,
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
      onerooms,
      clickedIndex: -1,
    };
  },
  methods: {
    increase(index) {
      this.singo[index]++;
    },
    handleRemoveModal() {
      this.showModal = false;
      this.clickedIndex = -1;
    },
    handleShowModal(index) {
      this.showModal = true;
      this.clickedIndex = index;
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
  top: 0;
  left: 0;
  padding: 20px;
}

.white-bg {
  width: 100%;
  background: white;
  border-radius: 8px;
  padding: 20px;
  z-index: 2;
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
import onerooms from "./assets/onerooms";

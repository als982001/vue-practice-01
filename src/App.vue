<template>
  <img alt="Vue logo" src="./assets/logo.png" />

  <div class="start" :class="{ end: showModal }">
    <div>ㅋㅋㅋㅋㅋ</div>
  </div>

  <Transition name="fade">
    <InfoModal
      :onerooms="onerooms"
      :showModal="showModal"
      :clickedIndex="clickedIndex"
      :handleCloseModal="handleCloseModal"
      @closeModal="
        console.log($event);
        handleCloseModal();
      "
    />
  </Transition>

  <h1 :style="titleStyle">원룸보여줌</h1>
  <Discount :discountValue="discountValue" />
  <div class="menu">
    <a v-for="(item, index) in menu" :key="item">{{ `${index}. ${item}` }}</a>
  </div>

  <div>
    <button @click="sortByPrice()">가격 순 정렬</button>
    <button @click="sortBack()">원래대로</button>
  </div>

  <ProductInfo
    v-for="(oneroom, index) in onerooms"
    :key="oneroom.title"
    :oneroom="oneroom"
    :handleShowModal="handleShowModal"
    :index="index"
    @openModal="
      showModal = true;
      clickedIndex = $event;
    "
  />
</template>

<script>
// import HelloWorld from "./components/HelloWorld.vue";
import onerooms from "./assets/onerooms";
import DiscountComponent from "./components/DiscountComponent.vue";
import InfoModal from "./components/InfoModal.vue";
import ProductInfo from "./components/ProductInfo.vue";

export default {
  name: "App",
  components: {
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
      onerooms: [...onerooms],
      originalOnerooms: [...onerooms],
      clickedIndex: -1,
      discountValue: 30,
    };
  },
  methods: {
    increase(index) {
      this.singo[index]++;
    },
    handleCloseModal() {
      this.showModal = false;
      this.clickedIndex = -1;
    },
    handleShowModal(index) {
      this.showModal = true;
      this.clickedIndex = index;
    },
    sortByPrice() {
      this.onerooms.sort((a, b) => a.price - b.price);
    },
    sortBack() {
      this.onerooms = [...this.originalOnerooms];
    },
  },
  mounted() {
    let decreaseDiscountId = setInterval(() => {
      --this.discountValue;

      if (this.discountValue <= 0) {
        clearInterval(decreaseDiscountId);
      }
    }, [1000]);
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

.start {
  opacity: 0;
  transition: all 1s;
}

.end {
  opacity: 1;
}

.fade-enter-from {
  opacity: 0;
}

.fade-enter-active {
  transition: all 1s;
}

.fade-enter-to {
  opacity: 1;
}

.fade-leave-from {
  opacity: 1;
}

.fade-leave-active {
  transition: all 3s;
}

.fade-leave-to {
  opacity: 0;
}
</style>

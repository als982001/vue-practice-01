<template>
  <div class="black-bg" v-if="showModal">
    <div class="white-bg">
      <img :src="onerooms[clickedIndex].image" class="room-img" />
      <h4>{{ onerooms[clickedIndex].title }}</h4>
      <p>{{ onerooms[clickedIndex].content }}</p>
      <input placeholder="달 입력" v-model="month" />
      <p>가격: {{ (100000 * Number(month)).toLocaleString() }}</p>
      <input placeholder="hahaha" @input="hahaha = $event.target.value" />
      <p>hahaha: {{ hahaha }}</p>
      <button @click="$emit('closeModal', { hahaha: 'hahaha' })">닫기</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "InfoModal",
  data() {
    return {
      month: "",
      hahaha: "",
    };
  },
  watch: {
    month(currentValue, beforeValue) {
      console.log(currentValue);
      console.log(typeof currentValue);

      if (isNaN(currentValue) == true) {
        alert("뭐함");
        this.month = 1;
      }

      console.log(`${beforeValue} => ${currentValue}`);
    },
  },
  updated() {
    if (this.month.includes("2")) {
      alert("2 안됨");
      this.month = "";
    }
  },
  props: {
    showModal: Boolean,
    clickedIndex: Number,
    onerooms: Array,
    handleCloseModal: Function,
  },
};
</script>

<style></style>
import { values } from 'core-js/core/array'; import { includes } from
'core-js/core/array';

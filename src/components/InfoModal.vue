<template>
  <div class="black-bg" v-if="showModal">
    <div class="white-bg">
      <img :src="onerooms[clickedIndex].image" class="room-img" />
      <h4>{{ onerooms[clickedIndex].title }}</h4>
      <p>{{ onerooms[clickedIndex].content }}</p>
      <input placeholder="달 입력" @input="month = $event.target.value" />
      <p>가격: {{ 100000 * month }}</p>
      <input placeholder="hahaha" v-model.number="hahaha" />
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
      month: 1,
      hahaha: "",
    };
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

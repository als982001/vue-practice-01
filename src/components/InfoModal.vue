<template>
  <div class="black-bg" v-if="showModal">
    <div class="white-bg">
      <img :src="onerooms[clickedIndex].image" class="room-img" />
      <h4>{{ onerooms[clickedIndex].title }}</h4>
      <p>{{ onerooms[clickedIndex].content }}</p>
      <button @click="$emit('closeModal')">닫기</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "InfoModal",
  props: {
    showModal: Boolean,
    clickedIndex: Number,
    onerooms: Array,
    handleCloseModal: Function,
  },
};
</script>

<style></style>

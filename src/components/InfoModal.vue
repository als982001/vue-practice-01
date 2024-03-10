<template>
  <div class="black-bg" v-if="showModal">
    <div class="white-bg">
      <h4>{{ onerooms[clickedIndex].title }}</h4>
      <p>{{ onerooms[clickedIndex].content }}</p>
      <button @click="handleRemoveModal()">닫기</button>
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
    handleRemoveModal: Function,
  },
};
</script>

<style></style>

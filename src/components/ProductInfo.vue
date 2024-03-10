<template>
  <img :src="oneroom.image" class="room-img" />
  <h4 @click="handleShowModal(index)">
    {{ oneroom.title }}
  </h4>
  <p>{{ oneroom.price }}원</p>
</template>

<script>
export default {
  name: "ProductInfo",
  props: {
    oneroom: Object,
    handleShowModal: Function,
    index: Number,
  },
};
</script>

<style>
.room-img {
  width: 100%;
}
</style>

<template>
  <div>
    <img :src="oneroom.image" class="room-img" />
    <h4 @click="openModal()">
      {{ oneroom.title }}
    </h4>
    <p>{{ oneroom.price }}원</p>
  </div>
</template>

<script>
export default {
  name: "ProductInfo",
  props: {
    oneroom: Object,
    handleShowModal: Function,
    index: Number,
  },
  methods: {
    openModal() {
      this.$emit("openModal", this.oneroom.id);
    },
  },
};
</script>

<style>
.room-img {
  width: 100%;
}
</style>

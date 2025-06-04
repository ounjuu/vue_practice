<template>
  <div>
    <img :src="product.image" class="room-img" @click="openModal" />
    <h4>{{ product.title }}</h4>
    <p>{{ product.price }} 만원</p>
    <!-- <button @click="increase(product)">허위매물신고</button
    ><span>신고수 : {{ product.count }}</span> -->
  </div>
</template>

<script>
export default {
  name: "Card",
  props: {
    product: Object,
    index: Number,
    itemnum: Number,
    handleModal: Boolean,
  },
  methods: {
    openModal() {
      this.$emit("open", this.index);
    },
  },
};
</script>
<style></style>

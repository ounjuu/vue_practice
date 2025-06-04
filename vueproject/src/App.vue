<template>
  <div>
    <div v-for="product in products">
      <h4>{{ product.name }}</h4>
      <p>{{ product.price }} 만원</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      products: [
        { name: "역삼동 원룸", price: 60 },
        { name: "천호동 원룸", price: 50 },
        { name: "마포구 원룸", price: 80 },
      ],
    };
  },
  components: {},
};
</script>

<style></style>

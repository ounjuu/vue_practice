<template>
  <div class="menu">
    <a v-for="(menuname, index) in menus" :key="index">{{ menuname }}</a>
  </div>
  <div v-for="(product, index) in products" :key="index">
    <h4>{{ product.name }}</h4>
    <p>{{ product.price }} 만원</p>
    <button @:click="increase(product)">허위매물신고</button
    ><span>신고수 : {{ product.count }}</span>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      products: [
        { name: "역삼동 원룸", price: 60, count: 0 },
        { name: "천호동 원룸", price: 50, count: 0 },
        { name: "마포구 원룸", price: 80, count: 0 },
      ],
      menus: ["Home", "Shop", "About"],
    };
  },
  methods: {
    increase(product) {
      product.count++;
    },
  },
  components: {},
};
</script>

<style>
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

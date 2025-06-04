<template>
  <!-- 상단 메뉴바 -->
  <div class="menu">
    <a v-for="(menuname, index) in menus" :key="index">{{ menuname }}</a>
  </div>

  <!-- 배너 -->
  <Discount />

  <!-- 상품들 -->
  <Card
    v-for="(product, index) in onerooms"
    :key="index"
    :product="product"
    :index="index"
    :itemnum="itemnum"
    :handleModal="handleModal"
    @open="
      (idx) => {
        handleModal = true;
        itemnum = idx;
      }
    "
  />

  <!-- 모달 -->
  <Modal
    :onerooms="onerooms"
    :itemnum="itemnum"
    :handleModal="handleModal"
    @close="handleModal = false"
  />
</template>

<script>
import room0 from "@/assets/room0.jpg";
import room1 from "@/assets/room1.jpg";
import room2 from "@/assets/room2.jpg";

import roomdata from "@/assets/oneroom";
import Discount from "./Discount.vue";
import Modal from "./Modal.vue";
import Card from "./Card.vue";

export default {
  name: "App",
  data() {
    return {
      itemnum: 0,
      onerooms: roomdata,
      products: [
        { name: "역삼동 원룸", price: 60, count: 0, img: room0 },
        { name: "천호동 원룸", price: 50, count: 0, img: room1 },
        { name: "마포구 원룸", price: 80, count: 0, img: room2 },
      ],
      menus: ["Home", "Shop", "About"],
      handleModal: false,
    };
  },
  methods: {
    increase(product) {
      product.count++;
    },
  },
  components: {
    Discount: Discount,
    Modal: Modal,
    Card: Card,
  },
};
</script>

<style>
body {
  margin: 0;
}
div {
  box-sizing: border-box;
}
.discount {
  background-color: #eee;
  padding: 10px;
  margin: 10px;
  border-radius: 5px;
  display: flex;
  justify-content: center;
  align-items: center;
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
.room-img {
  padding-top: 25px;
  width: 350px;
  aspect-ratio: 2/1;
}
</style>

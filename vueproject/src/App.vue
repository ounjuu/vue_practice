<template>
  <div class="menu">
    <a v-for="(menuname, index) in menus" :key="index">{{ menuname }}</a>
  </div>
  <div v-for="(product, index) in onerooms" :key="index">
    <img :src="product.image" class="room-img" @click="handleModal = true" />
    <h4>{{ product.title }}</h4>
    <p>{{ product.price }} 만원</p>
    <!-- <button @click="increase(product)">허위매물신고</button
    ><span>신고수 : {{ product.count }}</span> -->
  </div>
  <div class="black-bg" v-if="handleModal === true">
    <div class="white-bg">
      <h4>상세페이지</h4>
      <p>상세페이지내용임</p>
      <button @click="handleModal = false">닫기</button>
    </div>
  </div>
</template>

<script>
import room0 from "@/assets/room0.jpg";
import room1 from "@/assets/room1.jpg";
import room2 from "@/assets/room2.jpg";

import roomdata from "@/assets/oneroom";

export default {
  name: "App",
  data() {
    return {
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
  components: {},
};
</script>

<style>
body {
  margin: 0;
}
div {
  box-sizing: border-box;
}
.black-bg {
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  position: fixed;
  padding: 20px;
  top: 0;
  left: 0;
  z-index: 10;
  display: flex;
  justify-content: center;
  align-items: center;
}
.white-bg {
  width: 100%;
  background: white;
  border-radius: 8px;
  padding: 20px;
  height: 80vh;
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

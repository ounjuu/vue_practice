<template>
  <!-- 상단 메뉴바 -->
  <div class="menu">
    <a v-for="(menuname, index) in menus" :key="index">{{ menuname }}</a>
  </div>

  <!-- 배너 -->
  <Discount :discount="discount" v-if="discount >= 0" />

  <!-- 가격순 버튼 -->
  <button @click="priceSort">가격순정렬</button>
  <button @click="sortBack">되돌리기</button>

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
  <!-- <div class="start" :class="{ end: handleModal }"> -->
  <!-- 위에 코드 대신 transition 사용 가능 -->
  <transition name="fade">
    <Modal
      :onerooms="onerooms"
      :itemnum="itemnum"
      :handleModal="handleModal"
      @close="handleModal = false"
    />
  </transition>
  <!-- </div> -->
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
      oneroomsOriginal: [...roomdata],
      onerooms: roomdata,
      products: [
        { name: "역삼동 원룸", price: 60, count: 0, img: room0 },
        { name: "천호동 원룸", price: 50, count: 0, img: room1 },
        { name: "마포구 원룸", price: 80, count: 0, img: room2 },
      ],
      menus: ["Home", "Shop", "About"],
      handleModal: false,
      showDiscount: 30,
      discount: 30,
    };
  },
  methods: {
    increase(product) {
      product.count++;
    },
    priceSort() {
      this.onerooms.sort(function (a, b) {
        return a.price - b.price;
      });
    },
    sortBack() {
      this.onerooms = [...this.oneroomsOriginal];
    },
  },
  mounted() {
    setInterval(() => {
      this.discount--;
      if (this.discount < 0) {
        clearInterval(this.interval);
      }
    }, 1000);
  },
  beforeUnmount() {
    clearInterval(this.interval);
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
/* 애니메이션 효과 */
/* .start {
  opacity: 0;
  transition: all 1s;
}
.end {
  opacity: 1;
} */
.fade-enter-from {
  opacity: 0;
}
.fade-enter-active {
  transition: all 1s;
}
.fade-enter-to {
  opacity: 1;
}
.fade-leave-from {
  opacity: 1;
}
.fade-leave-active {
  transition: all 1s;
}
.fade-leave-to {
  opacity: 0;
}
</style>

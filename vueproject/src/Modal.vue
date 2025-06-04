<template>
  <div class="black-bg" v-if="handleModal && handleModal === true">
    <div class="white-bg">
      <img :src="onerooms[itemnum].image" />
      <h4>{{ onerooms[itemnum].title }}</h4>
      <!-- <input @input="month = $event.target.value" /> -->
      <input v-model.number="month" />
      <p>{{ month }}개월 선택함 : {{ onerooms[itemnum].price * month }}원</p>
      <p>{{ onerooms[itemnum].content }}</p>

      <button @click="$emit('close')">닫기</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "Modal",
  props: {
    onerooms: Array,
    itemnum: Number,
    handleModal: Boolean,
  },
  data() {
    return {
      month: 1,
    };
  },
};
</script>
<style>
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
  width: 80%;
  background: white;
  border-radius: 8px;
  padding: 40px 20px;
  height: 90vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  img {
    width: 50%;
    aspect-ratio: 2/1;
  }
}
</style>

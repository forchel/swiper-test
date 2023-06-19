<script setup lang="ts">
import SwiperSample from './components/SwiperSample.vue'
</script>

<template>
  <img alt="Vue logo" src="./assets/logo.png" />
  <SwiperSample msg="Swiper Sample + Vue 3 + TypeScript + Vite">
    <template v-for="index in [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]">
      <div class="swiper-slide">{{ index }}</div>
    </template>
  </SwiperSample>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.swiper-slide {
  background: #f1f1f1;
  color: #000;
  text-align: center;
  line-height: 300px;
}

</style>

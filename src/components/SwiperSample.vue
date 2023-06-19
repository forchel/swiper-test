<script setup lang="ts">
import { ref, Ref, watchEffect } from 'vue';
// eslint-disable-next-line import/no-named-as-default
import Swiper, { Navigation, Pagination, Zoom } from 'swiper';
import {NavigationOptions, PaginationOptions, SwiperModule} from 'swiper/types';
import { SwiperSlide } from 'swiper/vue/swiper-vue.js';

defineProps<{ msg: string }>()

const swiper: Ref<HTMLElement | undefined> = ref();
const mainPrev: Ref<HTMLElement | undefined> = ref();
const mainNext: Ref<HTMLElement | undefined> = ref();
const swiperPagination: Ref<HTMLElement | undefined> = ref();

watchEffect(() => {
  if (swiper.value) {

    // install Swiper modules
    const modules: SwiperModule[] = [Navigation, Pagination, Zoom];

    const mainNavigation: NavigationOptions = {
      nextEl: mainNext.value,
      prevEl: mainPrev.value,
    };

    const pagination: PaginationOptions = {
      el: swiperPagination.value,
      type: 'progressbar',
      clickable: true,
    };

    new Swiper(swiper.value, {
      breakpoints: {
        576: {
        },
        840: {
        },
        1080: {
        },
        1300: {
        },
        1600: {
        }
      },
      slidesPerView: 1,
      spaceBetween: 32,
      zoom: {
        maxRatio: 2,
      },
      createElements: true,
      loop: false,
      grabCursor: true,
      pagination: pagination,
      navigation: mainNavigation,
      modules: modules
    });
  }

});

</script>

<template>
  <h1>{{ msg }}</h1>
    <div ref="swiper" class="swiper">
      <div ref="mainPrev" class="swiper-button-prev" />
      <div ref="mainNext" class="swiper-button-next" />
      <div ref="swiperPagination" class="swiper-pagination" />
      <div class="swiper-wrapper">
        <slot />
      </div>
    </div>

</template>

<style scoped>

.swiper {
  width: 100%;
  height: 300px;
  margin: 50px auto;
}

a {
  color: #42b983;
}

label {
  margin: 0 0.5em;
  font-weight: bold;
}

code {
  background-color: #eee;
  padding: 2px 4px;
  border-radius: 4px;
  color: #304455;
}

</style>

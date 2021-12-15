<template>
  <h1>{{ msg }}</h1>
  <div class="swiper-container-wrapper">
    <div ref="swiperContainer" class="swiper">
      <slot />
      <div ref="mainPrev" class="swiper-button-prev" />
      <div ref="mainNext" class="swiper-button-next" />
    </div>
    <div ref="swiperPagination" class="swiper-pagination" />
  </div>
</template>

<script setup lang="ts">
import { provide, ref, Ref, toRefs, watchEffect } from 'vue';
// eslint-disable-next-line import/no-named-as-default
import Swiper, { Lazy, Navigation, Pagination, Zoom } from 'swiper';
import { NavigationOptions, PaginationOptions } from 'swiper/types';

defineProps<{ msg: string }>()

const swiperContainer: Ref<HTMLElement | undefined> = ref();
const mainPrev: Ref<HTMLElement | undefined> = ref();
const mainNext: Ref<HTMLElement | undefined> = ref();
const swiperPagination: Ref<HTMLElement | undefined> = ref();

watchEffect(() => {
  if (swiperContainer.value) {

    // install Swiper modules
    Swiper.use([Navigation, Pagination, Lazy, Zoom]);
    // or since version 7.0.0
    // const modules: SwiperModule[] = [Navigation, Pagination, Lazy, Zoom];

    const mainNavigation: NavigationOptions = {
      nextEl: mainNext.value,
      prevEl: mainPrev.value,
    };

    const pagination: PaginationOptions = {
      el: swiperPagination.value,
      type: 'progressbar',
      clickable: true,
    };

    new Swiper(swiperContainer.value, {
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
      preloadImages: false,
      lazy: true,
    });
  }

});



</script>
<style scoped>
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

<template>
  <swiper
    :modules="modules"
    :speed="1500"
    :autoheight="false"
    :slides-per-view="1"
    :space-between="0"
    :autoplay="{
      delay: 2500,
      disableOnInteraction: false,
    }"
    :breakpoints="{
      '640': {
        slidesPerView: 1,
        spaceBetween: 0,
      },
      '768': {
        slidesPerView: 2,
        spaceBetween: 0,
      },
      '1024': {
        slidesPerView: 3,
        spaceBetween: 0,
      },
    }"

    :navigation="true"
    @swiper="onSwiper"
    @slideChange="onSlideChange"
  >

    <swiper-slide v-for="item in items" :key="item.id">
      <div class="h-100" v-if="!item.match('mp4')">
        <img :src="item" alt="sein video">
      </div>
      <div class="h-100" v-if="item.match('mp4')">
        <video autoplay playsinline loop muted width="100%" height="100%" onContextMenu="return false;">
          <source :src="item" type="video/mp4">
        </video>
      </div>
    </swiper-slide>

  </swiper>
</template>
<script>
  // import Swiper core and required modules
  import { Autoplay, Navigation, Pagination, Scrollbar, A11y } from 'swiper/modules';

  // Import Swiper Vue.js components
  import { Swiper, SwiperSlide } from 'swiper/vue';

  // Import Swiper styles
  import 'swiper/css';
  import 'swiper/css/navigation';
  import 'swiper/css/pagination';
  import 'swiper/css/scrollbar';

  // Import Swiper styles
  export default {
    components: {
      Swiper,
      SwiperSlide,
    },
    data() {
      return {
        items: [
          'src/assets/Celestial harmony.mp4',
          'src/assets/Keyboard.mp4',
          'src/assets/Clipan Finance Award/bumper-logo-cfi.mp4',
          'src/assets/Ibox/Ibox-logo.mp4',
          'src/assets/Magnum Ice/magnum Ice.mp4',
          'src/assets/Tiger Beer Soju/Tiger beer Soju.mp4'
        ]
      }
    },
    setup() {
      const onSwiper = (swiper) => {
        console.log(swiper);
      };
      const onSlideChange = () => {
        console.log('slide change');
      };
      return {
        onSwiper,
        onSlideChange,
        modules: [Autoplay, Navigation, Pagination, Scrollbar, A11y],
      };
    },
  };
</script>

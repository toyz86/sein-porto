<template>
  <swiper
    :modules="modules"
    :slides-per-view="1"
    :space-between="10"
    :breakpoints="{
      '640': {
        slidesPerView: 1,
        spaceBetween: 10,
      },
      '768': {
        slidesPerView: 2,
        spaceBetween: 10,
      },
      '1024': {
        slidesPerView: 5,
        spaceBetween: 30,
      },
    }"
    navigation
    @swiper="onSwiper"
    @slideChange="onSlideChange"
  >

    <!-- Thumbnail Video -->
    <swiper-slide v-for="(item, index) in items" :key="index" class="my-5">
      <div class="v-thumbnail h-100">
        <div class="play-icon" @click="onPlay(index)">
          <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 384 512">
            <path fill="#ffffff" d="M73 39c-14.8-9.1-33.4-9.4-48.5-.9S0 62.6 0 80V432c0 17.4 9.4 33.4 24.5 41.9s33.7 8.1 48.5-.9L361 297c14.3-8.7 23-24.2 23-41s-8.7-32.2-23-41L73 39z"/>
          </svg>
        </div>
        <img :src="item.thumb" alt="sein video">
      </div>
      <div class="video-title m-3">
        <h6>{{ item.title }}</h6>
      </div>
    </swiper-slide>

  </swiper>

  <div v-if="selectedVideo !== null" class="modal-video" v-show="showModal">
    <div class="container">
      <div class="close" @click="closeModal"></div>
      <div class="next-prev-buttons">
        <button @click="prevVideo" :disabled="currentIndex === 0" class="btn-prev">
          <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 320 512"><path d="M9.4 233.4c-12.5 12.5-12.5 32.8 0 45.3l192 192c12.5 12.5 32.8 12.5 45.3 0s12.5-32.8 0-45.3L77.3 256 246.6 86.6c12.5-12.5 12.5-32.8 0-45.3s-32.8-12.5-45.3 0l-192 192z"/></svg>
        </button>
        <button @click="nextVideo" :disabled="currentIndex === items.length - 1" class="btn-next">
          <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 320 512"><path d="M310.6 233.4c12.5 12.5 12.5 32.8 0 45.3l-192 192c-12.5 12.5-32.8 12.5-45.3 0s-12.5-32.8 0-45.3L242.7 256 73.4 86.6c-12.5-12.5-12.5-32.8 0-45.3s32.8-12.5 45.3 0l192 192z"/></svg>
        </button>
      </div>
      <div class="row">
        <div class="video-overlay">
          <transition name="slide" @before-enter="beforeEnter" @enter="enter" @before-leave="beforeLeave" @leave="leave">
            <video autoplay playsinline loop muted @contextmenu.prevent :key="selectedVideo">
              <source :src="selectedVideo" type="video/mp4">
            </video>
          </transition>
        </div>
        <div class="video-content">
          <h4>{{ selectedTitleVideo }}</h4>
        </div>
      </div>
    </div>
  </div>

</template>

<script>
  // import Swiper core and required modules
  import { Navigation, Pagination, Scrollbar, A11y } from 'swiper/modules';

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
          {
            src: 'src/assets/MMK-Merry Christmas 3.mp4',
            thumb: 'src/assets/audi.jpg',
            title: `MMK-Merry Christmas`
          },
          {
            src: 'src/assets/Magnum Ice/magnum Ice.mp4',
            thumb: 'src/assets/Magnum Ice/magnum Ice_thumbnail.png',
            title: 'Magnum Ice'
          },
          {
            src: 'src/assets/Clipan Finance Award/BUMPER PIALA CFI.mp4',
            thumb: 'src/assets/Clipan Finance Award/CFI-Plakat.png',
            title: 'BUMPER PIALA CFI'
          },
          {
            src: 'src/assets/Gojek/Inflate Animation - Gojek.mp4',
            thumb: 'src/assets/Gojek/Inflate Animation - Gojek0054.png',
            title: `Inflate Animation - Gojek`
          },
          {
            src: 'src/assets/Cream/Cream.mp4',
            thumb: 'src/assets/Cream/cream.png',
            title: 'Cream'
          },
          {
            src: 'src/assets/Ibox/Ibox-iphone.mp4',
            thumb: 'src/assets/Keyvisual-Alfa-Romeo-Giulia.jpg',
            title: 'Ibox iphone'
          },
          {
            src: 'src/assets/Ibox/Ibox-logo.mp4',
            thumb: 'src/assets/Ibox/Ibox-iphone.png',
            title: `Ibox logo Animation`
          },
          {
            src: 'src/assets/Marjan/Marjan.mp4',
            thumb: 'src/assets/Marjan/Preview/marjan-4.png',
            title: 'Marjan Animation'
          },
          {
            src: 'src/assets/Tiger Beer Soju/Tiger Soju Launch.mp4',
            thumb: 'src/assets/Tiger Beer Soju/workbench.png',
            title: 'Tiger Beer Soju Animation'
          },
          {
            src: 'src/assets/Tiger Beer Soju/TigerSoju-Sequnce-1.mp4',
            thumb: 'src/assets/Keyvisual-Alfa-Romeo-Giulia.jpg',
            title: ` Tiger Beer Soju Animation`
          },
          {
            src: 'src/assets/Tiger Beer Soju/Tiger Soju-bottle.mp4',
            thumb: 'src/assets/audi.jpg',
            title: ' Tiger Beer Soju Animation'
          },
          {
            src: 'src/assets/Unreal/MoverseReporter.mp4',
            thumb: 'src/assets/Unreal/Reporter.jpg',
            title: ' Moverse Reporter'
          },
          {
            src: 'src/assets/Unreal/TabrakMasuk_Moverse.mp4',
            thumb: 'src/assets/Unreal/TabrakMasuk.jpg',
            title: ' Moverse Jokowi'
          },
          {
            src: 'src/assets/Celestial harmony.mp4',
            thumb: 'src/assets/Celestical-Harmony.png',
            title: ' Celestical Harmony'
          },
          {
            src: 'src/assets/Fluid Bubble.mp4',
            thumb: 'src/assets/Fliud-Bubble.png',
            title: ' Fluid Bubble'
          },

        ],
        selectedVideo: null,
        selectedTitleVideo: null,
        showModal: false,
        currentIndex: null, 
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
        modules: [Navigation, Pagination, Scrollbar, A11y],
      };
    },
    methods: {
      beforeEnter(el) {
        el.style.transform = 'translateX(200%)'; 
      },
      enter(el, done) {
        setTimeout(() => {
          el.style.transition = 'transform 0.5s ease';
          el.style.transform = 'translateX(0)'; 
          done();
        }, 50); 
      },
      beforeLeave(el) {
        el.style.transition = 'transform 0.5s ease';
        el.style.transform = 'translateX(-200%)'; 
      },
      leave(el, done) {
        setTimeout(() => {
          done();
        }, 100);
      },

      onPlay(index) {
        // Set the selected video when the play icon is clicked
        this.selectedVideo = this.items[index].src;
        this.selectedTitleVideo = this.items[index].title;
        this.currentIndex = index;
        this.showModal = true;
      },
      closeModal() {
        // Close the modal
        this.showModal = false;
        this.selectedVideo = null;
        this.currentIndex = null;
      },
      nextVideo() {
        // Display the next video in the modal
        if (this.currentIndex < this.items.length - 1) {
          this.currentIndex++;
          this.selectedVideo = this.items[this.currentIndex].src;
          this.selectedTitleVideo = this.items[this.currentIndex].title;
        }
      },
      prevVideo() {
        // Display the previous video in the modal
        if (this.currentIndex > 0) {
          this.currentIndex--;
          this.selectedVideo = this.items[this.currentIndex].src;
          this.selectedTitleVideo = this.items[this.currentIndex].title;
        }
      },
    }
  };
</script>

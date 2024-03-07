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
      <div class="row">
        <!-- <video autoplay playsinline loop muted width="100%" height="100%" onContextMenu="return false;">
          <source :src="selectedVideo" type="video/mp4">
        </video> -->
        <div class="col-12 col-md-8">
          <iframe height="480" width="500"
            :src="selectedVideo">
          </iframe>
        </div>
        <div class="col-6 col-md-4 video-content">
          <h4>{{ selectedTitleVideo }}</h4>
        </div>
      </div>
    </div>

    <div class="thumbnail-bottom container-fluid">
      <swiper
        :modules="modules"
        :slides-per-view="8"
        :space-between="15"
        navigation
        @swiper="onSwiper"
        @slideChange="onSlideChange"
      >
  
        <!-- Thumbnail Video -->
        <swiper-slide v-for="(item, index) in items" :key="index" class="my-5" @click="onPlay(index)">
          <div class="v-thumbnail h-100">
            <div class="play-icon">
              <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 384 512">
                <path fill="#ffffff" d="M73 39c-14.8-9.1-33.4-9.4-48.5-.9S0 62.6 0 80V432c0 17.4 9.4 33.4 24.5 41.9s33.7 8.1 48.5-.9L361 297c14.3-8.7 23-24.2 23-41s-8.7-32.2-23-41L73 39z"/>
              </svg>
            </div>
            <img :src="item.thumb" alt="sein video">
          </div>
        </swiper-slide>
  
      </swiper>
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
            src: 'https://www.youtube.com/embed/il_t1WVLNxk',
            thumb: '/src/assets/audi.jpg',
            title: `Video 1 | Explore LiteVFX's top-tier 3D Breakdowns, setting the standard for TVC visual effects in Indonesia`
          },
          {
            src: 'https://www.youtube.com/embed/9HqOXpJryPs?si=F4gt6NASsOy9WP3A',
            thumb: '/src/assets/Keyvisual-Alfa-Romeo-Giulia.jpg',
            title: 'Video 2 | Ngewe sama tante'
          },
          {
            src: 'https://www.youtube.com/embed/E0Tf0fb2tD0?si=PTUr5vUT-huhylTF',
            thumb: '/src/assets/audi.jpg',
            title: 'Video 3 | Tante Cantik Berbagi Silit'
          },
          {
            src: 'https://www.youtube.com/embed/il_t1WVLNxk',
            thumb: '/src/assets/Keyvisual-Alfa-Romeo-Giulia.jpg',
            title: `Video 4 | Explore LiteVFX's top-tier 3D Breakdowns`
          },
          {
            src: 'https://www.youtube.com/embed/il_t1WVLNxk',
            thumb: '/src/assets/audi.jpg',
            title: 'Video 5 | setting the standard for TVC visual effects in Indonesia'
          },
          {
            src: 'https://www.youtube.com/embed/il_t1WVLNxk',
            thumb: '/src/assets/Keyvisual-Alfa-Romeo-Giulia.jpg',
            title: 'Video 6 | Main sama Bu Boss'
          },
          {
            src: 'https://www.youtube.com/embed/il_t1WVLNxk',
            thumb: '/src/assets/audi.jpg',
            title: `Video 7 | Explore LiteVFX's top-tier 3D Breakdowns, setting the standard for TVC visual effects in Indonesia`
          },
          {
            src: 'https://www.youtube.com/embed/il_t1WVLNxk',
            thumb: '/src/assets/Keyvisual-Alfa-Romeo-Giulia.jpg',
            title: 'Video 8 | Ngewe sama tante'
          },
          {
            src: 'https://www.youtube.com/embed/il_t1WVLNxk',
            thumb: '/src/assets/audi.jpg',
            title: 'Video 9 | Tante Cantik Berbagi Silit'
          },
          {
            src: 'https://www.youtube.com/embed/il_t1WVLNxk',
            thumb: '/src/assets/Keyvisual-Alfa-Romeo-Giulia.jpg',
            title: `Video 10 | Explore LiteVFX's top-tier 3D Breakdowns`
          },
          {
            src: 'https://www.youtube.com/embed/il_t1WVLNxk',
            thumb: '/src/assets/audi.jpg',
            title: 'Video 11 | setting the standard for TVC visual effects in Indonesia'
          },
          {
            src: 'https://www.youtube.com/embed/il_t1WVLNxk',
            thumb: '/src/assets/Keyvisual-Alfa-Romeo-Giulia.jpg',
            title: 'Video 12 | Main sama Bu Boss'
          },

        ],
        selectedVideo: null,
        selectedVideoTitle: null,
        showModal: false,
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
      onPlay(index) {
        // Set the selected video when the play icon is clicked
        this.selectedVideo = this.items[index].src;
        this.selectedTitleVideo = this.items[index].title;
        this.showModal = true;
      },
      closeModal() {
        // Close the modal
        this.showModal = false;
      },
    }
  };
</script>

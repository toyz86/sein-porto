<script setup>
import Header from './components/Header.vue';
import Myswiper from './components/Slider.vue';
import VideoList from './components/Videos.vue';
</script>

<template>
  <div>
    <Header id="navbar" :style="{ top: navbarTop }"></Header>
    <div class="section0">
      <div class="container">
        <div class="hero-wrapper" id="mainsection">
          <h1>sainimation</h1>
          <h2>Passionate Animator & Motion Designer <br> Bringing Stories to Life in the Digital Realm</h2>
          <!-- <p>
            As detail-oriented visual effects producers, we have gained valuable experience through a variety of commercials and media projects. Established in 2007, Lite Production has been one of the leading companies based in Jakarta in visual effects CGI. We love to co-work with directors and production houses to help out with visual that is impossible to be done with a conventional technique.
          </p> -->
        </div>
      </div>
  
      <div id="swiper" class="mt-5">
        <Myswiper />
      </div>
    </div>

    <div class="bg-fixed" id="feature">
      <div class="text-absolute container text-center">
        <h2>Featured - Marjan</h2>
        <p>A "Superbowl" season for Indonesian television, Marjan for Ramadan 2022. We did CGI for the whole episode (3 episodes in total) by replacing the environment, the main character weapon, building, Wereng craft, etc. This commercial was composed by Seto Harianto</p>
      </div>
      <!-- <div class="luxy-el" data-speed-y="5" data-offset="-50"> -->
        <video autoplay no-controls muted playsinline loop src="/src/assets/Unreal/MoverseReporter.mp4" style="height: 100%; width: 100%; object-fit: cover; object-position: center center; opacity: 1;"></video>
      <!-- </div> -->
    </div>

    <div id="section-about" class="container text-center">
      <h2 class="mb-5">About Us</h2>
      <p>
        As detail-oriented visual effects producers, we have gained valuable experience through a variety of commercials and media projects. Established in 2007, Lite Production has been one of the leading companies based in Jakarta in visual effects CGI. We love to co-work with directors and production houses to help out with visual that is impossible to be done with a conventional technique.
      </p>
    </div>

    <div class="bg-fixed text-center" id="breakdown">
      <div class="text-absolute container text-center">
        <h2>3D BREAKDOWN</h2>
        <p>Explore LiteVFX's top-tier 3D Breakdowns, setting the standard for TVC visual effects in Indonesia. Dive into a world of innovation and precision as LiteVFX transforms imagination into a captivating reality.</p>
      </div>
      <video autoplay no-controls muted playsinline loop src="/src/assets/Unreal/TabrakMasuk_Moverse.mp4" style="height: 100%; width: 100%; object-fit: cover; object-position: center center; opacity: 1;"></video>
    </div>

    <div class="video-lists pb-5" id="works">
      <VideoList />
    </div>

    <div id="contact" class="container text-center contact">
      <h2 class="mb-5">Contact</h2>
      <p>saintachirudin1899@gmail.com</p>
      <div class="sosmed-wrapper">
        <div class="d-flex justify-content-center">
          <div class="icon">
            <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 512 512">
              <path fill="#ffffff" d="M512 256C512 114.6 397.4 0 256 0S0 114.6 0 256C0 376 82.7 476.8 194.2 504.5V334.2H141.4V256h52.8V222.3c0-87.1 39.4-127.5 125-127.5c16.2 0 44.2 3.2 55.7 6.4V172c-6-.6-16.5-1-29.6-1c-42 0-58.2 15.9-58.2 57.2V256h83.6l-14.4 78.2H287V510.1C413.8 494.8 512 386.9 512 256h0z"/>
            </svg>
          </div>
          <div class="icon">
            <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 448 512">
              <path fill="#ffffff" d="M224.1 141c-63.6 0-114.9 51.3-114.9 114.9s51.3 114.9 114.9 114.9S339 319.5 339 255.9 287.7 141 224.1 141zm0 189.6c-41.1 0-74.7-33.5-74.7-74.7s33.5-74.7 74.7-74.7 74.7 33.5 74.7 74.7-33.6 74.7-74.7 74.7zm146.4-194.3c0 14.9-12 26.8-26.8 26.8-14.9 0-26.8-12-26.8-26.8s12-26.8 26.8-26.8 26.8 12 26.8 26.8zm76.1 27.2c-1.7-35.9-9.9-67.7-36.2-93.9-26.2-26.2-58-34.4-93.9-36.2-37-2.1-147.9-2.1-184.9 0-35.8 1.7-67.6 9.9-93.9 36.1s-34.4 58-36.2 93.9c-2.1 37-2.1 147.9 0 184.9 1.7 35.9 9.9 67.7 36.2 93.9s58 34.4 93.9 36.2c37 2.1 147.9 2.1 184.9 0 35.9-1.7 67.7-9.9 93.9-36.2 26.2-26.2 34.4-58 36.2-93.9 2.1-37 2.1-147.8 0-184.8zM398.8 388c-7.8 19.6-22.9 34.7-42.6 42.6-29.5 11.7-99.5 9-132.1 9s-102.7 2.6-132.1-9c-19.6-7.8-34.7-22.9-42.6-42.6-11.7-29.5-9-99.5-9-132.1s-2.6-102.7 9-132.1c7.8-19.6 22.9-34.7 42.6-42.6 29.5-11.7 99.5-9 132.1-9s102.7-2.6 132.1 9c19.6 7.8 34.7 22.9 42.6 42.6 11.7 29.5 9 99.5 9 132.1s2.7 102.7-9 132.1z"/>
            </svg>
          </div>
          <div class="icon">
            <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 576 512">
              <path fill="#ffffff" d="M232 237.2c31.8-15.2 48.4-38.2 48.4-74 0-70.6-52.6-87.8-113.3-87.8H0v354.4h171.8c64.4 0 124.9-30.9 124.9-102.9 0-44.5-21.1-77.4-64.7-89.7zM77.9 135.9H151c28.1 0 53.4 7.9 53.4 40.5 0 30.1-19.7 42.2-47.5 42.2h-79v-82.7zm83.3 233.7H77.9V272h84.9c34.3 0 56 14.3 56 50.6 0 35.8-25.9 47-57.6 47zm358.5-240.7H376V94h143.7v34.9zM576 305.2c0-75.9-44.4-139.2-124.9-139.2-78.2 0-131.3 58.8-131.3 135.8 0 79.9 50.3 134.7 131.3 134.7 61.3 0 101-27.6 120.1-86.3H509c-6.7 21.9-34.3 33.5-55.7 33.5-41.3 0-63-24.2-63-65.3h185.1c.3-4.2 .6-8.7 .6-13.2zM390.4 274c2.3-33.7 24.7-54.8 58.5-54.8 35.4 0 53.2 20.8 56.2 54.8H390.4z"/>
            </svg>
          </div>
        </div>
      </div>
    </div>

  </div>
</template>

<script>
import luxy from "luxy.js"
// import gsap from "/src/assets/gsap/gsap.min.js";
// import SplitText from "/src/assets/gsap/SplitText.min.js";
export default {
  data() {
    return {
      prevScrollpos: window.pageYOffset,
      navbarTop: '0' // Initial position when the component is mounted
    }
  },
  mounted() {
    window.onscroll = this.handleScroll;

    gsap.registerPlugin(SplitText);

    const tl = gsap.timeline(),
      mySplitText = new SplitText("#mainsection", { type: "words,chars" }),
      chars = mySplitText.chars; //an array of all the divs that wrap each character

    gsap.set("#mainsection", { perspective: 400 });

    console.log(chars);

    tl.from(chars, {
      duration: 0.8,
      opacity: 0,
      scale: 0,
      y: 80,
      rotationX: 180,
      transformOrigin: "0% 50% -50",
      ease: "back",
      stagger: 0.01
    });

  },
  methods: {
    handleScroll() {
      const currentScrollPos = window.pageYOffset;
  
      if (this.prevScrollpos > currentScrollPos) {
        this.navbarTop = '0';
      } else {
        this.navbarTop = '-150px';
      }
  
      this.prevScrollpos = currentScrollPos;
    }
  },
  beforeDestroy() {
    // Make sure to remove the scroll event listener when the component is destroyed
    window.removeEventListener('scroll', this.handleScroll);
  }

}
</script>
<style lang="scss">
  @import './assets/style.scss'
</style>
<template>
  <header>
    <div class="nav-wrapper">
      <div class="logo-nav">
        <h3>Sein<strong> Animation</strong></h3>
      </div>
      <div class="d-block d-lg-none">
        <div id="sidemenu">
          <button class="sidemenu__btn" v-on:click="navOpen=!navOpen" v-bind:class="{active:navOpen}">
              <span class="top"></span>
              <span class="mid"></span>
              <span class="bottom"></span>
            </button>
          <transition name="translateX">
            <nav v-show="navOpen">
              <div class="sidemenu__wrapper">
                <ul class="sidemenu__list">
                  <li class="sidemenu__item"><a href="#mainsection">Home</a></li>
                  <li class="sidemenu__item"><a href="#section-about">About</a></li>
                  <li class="sidemenu__item"><a href="#breakdown">3d Breadkdown</a></li>
                  <li class="sidemenu__item"><a href="#works">Our Works</a></li>
                  <li class="sidemenu__item"><a href="#contact">Contact</a></li>
                </ul>
              </div>
            </nav>
          </transition>
        </div>
      </div>
      <div class="menu-nav d-none d-lg-block">
        <ul>
          <li><a href="#mainsection">Home</a></li>
          <li><a href="#section-about">About</a></li>
          <li><a href="#breakdown">3d Breadkdown</a></li>
          <li><a href="#works">Our Works</a></li>
          <li><a href="#contact">Contact</a></li>
        </ul>
      </div>
    </div>
    <div class="blur"></div>
  </header>
</template>


<script>
  export default {
    data() {
      return {
        navOpen: false,
      }
    }
  }
</script>
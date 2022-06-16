<template>
  <swiper
    :centeredSlides="true"
    :lazy="true"
    :navigation="false"

    :autoplay="{
      delay: 2500,
      disableOnInteraction: false,
    }"

    :pagination="{
      dynamicBullets: true,
      clickable: true,
    }"
    :modules="modules"
    class="mySwiper"
    :style="{
      '--swiper-navigation-color': '#fff',
      '--swiper-pagination-color': '#fff',
    }"
  >
    <!-- <swiper-slide>
      <div class="single-hero-items set-bg">
        <img data-src="./assets/diskon-daily-1.png" alt="" />
      </div>
    </swiper-slide> -->
    <swiper-slide>
      <img src="../../public/img/diskon-daily-1.png" class="swiper-lazy" />
      <div class="swiper-lazy-preloader swiper-lazy-preloader-white"></div>
    </swiper-slide>
    <swiper-slide>
      <img src="../../public/img/diskon-daily-2.png" class="swiper-lazy" />
      <div class="swiper-lazy-preloader swiper-lazy-preloader-white"></div>
    </swiper-slide>
    <swiper-slide>
      <img src="../../public/img/diskon-daily-3.png" class="swiper-lazy" />
      <div class="swiper-lazy-preloader swiper-lazy-preloader-white"></div>
    </swiper-slide>
  </swiper>
</template>
<script>
// Import Swiper Vue.js components
import { Swiper, SwiperSlide } from "swiper/vue";

// Import Swiper styles
import "swiper/css";

import "swiper/css/pagination";
import "swiper/css/lazy";

import "swiper/css/pagination";
import "swiper/css/navigation";

// import required modules
import { Autoplay, Lazy, Pagination, Navigation } from "swiper";

export default {
  name: "CarrouselHome",
  components: {
    Swiper,
    SwiperSlide,
  },
  setup() {
    return {
      modules: [Autoplay, Lazy, Pagination, Navigation],
    };
  },
};
</script>

<style scoped>
header {
  width: 100%;
}
.swiper {
  width: 100%;
  height: 667px;
}

.swiper-slide {
  text-align: center;
  /* font-size: 18px; */
  background: #fff;

  /* Center slide text vertically */
  display: -webkit-box;
  display: -ms-flexbox;
  display: -webkit-flex;
  display: flex;
  -webkit-box-pack: center;
  -ms-flex-pack: center;
  -webkit-justify-content: center;
  justify-content: center;
  -webkit-box-align: center;
  -ms-flex-align: center;
  -webkit-align-items: center;
  align-items: center;
}

.swiper-slide img {
  width: 1920px;
  height: 667px;
  /* max-width: 100%;
  max-height: 100%; */
  -ms-transform: translate(-50%, -50%);
  -webkit-transform: translate(-50%, -50%);
  -moz-transform: translate(-50%, -50%);
  transform: translate(-50%, -50%);
  position: absolute;
  /* padding-left: 22px;
  padding-right: 12px; */
  left: 50%;
  top: 50%;
}
</style>
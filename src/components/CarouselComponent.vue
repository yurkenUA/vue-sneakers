<script>
import { Swiper, SwiperSlide } from 'swiper/vue'
import { Navigation, Pagination } from 'swiper/modules'

import 'swiper/css'
import 'swiper/css/navigation'
import 'swiper/css/pagination'

export default {
  components: {
    Swiper,
    SwiperSlide
  },
  setup() {
    return {
      modules: [Navigation, Pagination]
    }
  }
}
</script>

<template>
  <swiper
    :pagination="{
      dynamicBullets: true
    }"
    :navigation="true"
    :modules="modules"
    class="mySwiper"
  >
    <swiper-slide><img src="/image0.png" alt="Image 0" /></swiper-slide>
    <swiper-slide><img src="/image1.jpg" alt="Image 1" /></swiper-slide>
    <swiper-slide><img src="/image2.jpg" alt="Image 2" /></swiper-slide
    ><swiper-slide><img src="/image3.png" alt="Image 3" /></swiper-slide>
    <swiper-slide><img src="/image4.jpg" alt="Image 4" /></swiper-slide
    ><swiper-slide><img src="/image5.jpg" alt="Image 5" /></swiper-slide>
  </swiper>
  <!-- <div class="swiper">
    <div class="swiper-wrapper">
      <div class="swiper-slide"><img src="/image1.jpg" alt="Image 1" /></div>
      <div class="swiper-slide"><img src="/image2.jpg" alt="Image 2" /></div>
      <div class="swiper-slide"><img src="/image3.png" alt="Image 3" /></div>
      <div class="swiper-slide"><img src="/image4.jpg" alt="Image 4" /></div>
      <div class="swiper-slide"><img src="/image5.jpg" alt="Image 5" /></div>
    </div>
    <div class="swiper-pagination"></div>

    <div class="swiper-button-prev"></div>
    <div class="swiper-button-next"></div>

    <div class="swiper-scrollbar"></div>
  </div> -->
</template>

<style>
.swiper {
  margin: 20px auto;
  width: 960px;
  height: 300px;
  border-radius: 20px;
  cursor: pointer;
}

.swiper-slide {
  text-align: center;
  font-size: 18px;
  background: #fff;

  /* Center slide text vertically */
  display: flex;
  justify-content: center;
  align-items: center;
}

.swiper-slide img {
  display: block;
  width: 100%;
  height: 100%;
  object-fit: fill;
}
.swiper-button-prev,
.swiper-button-next {
  color: #a5d364;
}

.swiper-pagination-bullet {
  background-color: #a5d364;
}
</style>

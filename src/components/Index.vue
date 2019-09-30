<template lang="pug">
 div
  NavBar
  .single-bg
  .main.col-xs-12.col-sm-10.col-sm-offset-1.col-md-8.col-md-offset-2
    .row
      .col-xs-12
        swiper(:options="swiperOption")
            swiper-slide.slide-1(style="height:350px")
            swiper-slide.slide-2(style="height:350px")
            .swiper-pagination.swiper-pagination-white(slot="pagination")
            .swiper-button-prev.swiper-button-white(slot="button-prev")
            .swiper-button-next.swiper-button-white(slot="button-next")
</template>

<script>
import { swiper, swiperSlide } from "vue-awesome-swiper";
import "swiper/dist/css/swiper.css";
import NavBar from "@/components/NavBar";
export default {
  name: "Index",
  components: {
    NavBar,
    swiper,
    swiperSlide
  },
  data() {
    return {
      novels: [],
      swiperOption: {
        spaceBetween: 30,
        effect: "fade",
        pagination: {
          el: ".swiper-pagination",
          clickable: true
        },
        autoplay: {
          delay: 3000,
          disableOnInteraction: false
        },
        navigation: {
          nextEl: ".swiper-button-next",
          prevEl: ".swiper-button-prev"
        }
      }
    };
  }
};
</script>

<style>
</style>

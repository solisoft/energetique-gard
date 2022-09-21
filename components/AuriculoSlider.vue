<template>
  <section class="main-slider main-slider-two">
    <swiper ref="mySwiperTwo" :options="swiperOptions">
      <swiper-slide v-for="item in sliderTwo" :key="item.index">
        <div
          class="image-layer"
          :style="`
                background-image: url(${require(`~/assets/images${item.image}`)});
              `"
        ></div>
        <div class="image-layer-overlay"></div>
        <!-- /.image-layer -->
        <div class="container">
          <div class="row">
            <div class="col-lg-12 text-center">
            </div>
          </div>
        </div>
      </swiper-slide>
    </swiper>
    <!-- If we need navigation buttons -->
    <div class="swiper-pagination" id="main-slider-pagination"></div>

  </section>
</template>

<script>
import { Swiper, SwiperSlide, directive } from "vue-awesome-swiper";
import "swiper/css/swiper.css";
import data from "~/data/data.json";
export default {
  props: {
    slide: String
  },
  components: {
    Swiper,
    SwiperSlide,
  },
  directives: {
    swiper: directive,
  },
  data() {
    return {
      sliderTwo: data[this.$props.slide],
      sliderOneCounter: data.sliderOneCounter,
      swiperOptions: {
        slidesPerView: 1,
        loop: true,
        speed: 1000,
        effect: "fade",
        pagination: {
          el: "#main-slider-pagination",
          type: "bullets",
          clickable: true,
        },
        navigation: {
          nextEl: "#main-slider__swiper-button-next",
          prevEl: "#main-slider__swiper-button-prev",
        },
        autoplay: {
          delay: 5000,
          disableOnInteraction: false,
        },
      },
    };
  },
};
</script>

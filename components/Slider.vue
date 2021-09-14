<template>
  <client-only>
    <swiper class="slider" ref="mySwiper" :options="slider">
      <swiper-slide class="slider__slide" v-for="n in 4" :key="`slider-${n}`">
        <div class="container">
          <div class="slider__slide_slide-text slide-text">
            <h3>Баннерная зона</h3>
            <p>
              Why do we use it? It is a long established fact that a reader will
              be distracted by the readable
            </p>
            <button type="button">
              Button
            </button>
          </div>
        </div>
      </swiper-slide>
      <div class="swiper-pagination" slot="pagination"></div>
    </swiper>
  </client-only>
</template>

<script>
export default {
  name: "Slider",
  data() {
    return {
      slider: {
        autoplay: {
          delay: 5000
        },
        pagination: {
          el: ".swiper-pagination",
          clickable: true
        }
      }
    };
  },
  computed: {
    swiper() {
      return this.$refs.mySwiper.$swiper;
    }
  }
};
</script>

<style lang="scss" scoped>
/deep/.swiper-wrapper {
  height: 400px;
}
.slide-text {
  h3 {
    font-weight: 800;
    font-size: 48px;
    line-height: 65px;
    color: #000000;
    margin-bottom: 18px;
  }
  p {
    color: #4380e7;
    font-weight: 600;
    font-size: 18px;
    line-height: 25px;
    max-width: 377px;
    margin-bottom: 59px;
  }
  button {
    max-width: 254px;
    width: 100%;
    height: 54px;
    display: flex;
    justify-content: center;
    align-items: center;
    color: #fff;
    font-weight: 800;
    font-size: 18px;
    line-height: 25px;
    background: #1bceb6;
    border-radius: 10px;
    border: none;
    cursor: pointer;
  }
}
</style>

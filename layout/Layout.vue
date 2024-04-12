<script setup lang="ts">
let intervalId: ReturnType<typeof setInterval>;
const slide = ref("6.png");
const slides = ref(["1.png", "2.png", "3.png", "4.webp", "5.webp", "6.png"]);

const advancedSlide = () => {
  const currentIndex = slides.value.findIndex((s) => s === slide.value);
  const nextIndex = (currentIndex + 1) % slides.value.length;
  slide.value = slides.value[nextIndex];
};

onMounted(() => (intervalId = setInterval(advancedSlide, 5000)));
onUnmounted(() => clearInterval(intervalId));
</script>

<template>
  <div class="full-screen-carousel">
    <q-carousel
      v-model="slide"
      transition-prev="slide-right"
      transition-next="slide-left"
      animated
      control-color="primary"
      class="custom-carousel"
    >
      <q-carousel-slide v-for="item in slides" :key="item" :name="item">
        <img :src="'/images/' + item" class="h-full w-full object-contain" />
      </q-carousel-slide>
    </q-carousel>
    <div class="overlay-content">
      <Navbar />
      <slot></slot>
    </div>
  </div>
</template>

<style scoped>
.full-screen-carousel {
  position: relative;
  height: 100vh;
  width: 100vw;
  padding-top: 50px;
}

.custom-carousel {
  height: 100%;
  width: 100%;
}

.overlay-content {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: column;
}

img {
  opacity: 0.25;
  height: 100%;
  width: 100%;
  object-fit: contain;
}
</style>

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
  <div class="fixed inset-0 z-0">
    <q-carousel
      v-model="slide"
      transition-prev="slide-right"
      transition-next="slide-left"
      animated
      class="h-full w-full object-contain"
    >
      <q-carousel-slide v-for="item in slides" :key="item" :name="item">
        <img :src="'/images/' + item" class="h-full w-full object-contain" />
      </q-carousel-slide>
    </q-carousel>
  </div>

  <slot></slot>
</template>

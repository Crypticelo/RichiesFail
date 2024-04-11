<template>
  <Navbar></Navbar>
  <div class="q-pa-md">
    <q-carousel
      v-model="slide"
      transition-prev="slide-right"
      transition-next="slide-left"
      animated
      control-color="primary"
      class="rounded-lg overflow-hidden relative custom-carousel"
    >
      <q-carousel-slide
        name="style"
        class="relative overflow-hidden flex justify-center items-center h-full"
      >
        <img
          src="/image/first.png"
          alt="Style"
          class="h-full w-auto max-w-none"
        />
      </q-carousel-slide>
      <q-carousel-slide
        name="tv"
        class="relative overflow-hidden flex justify-center items-center h-full"
      >
        <img
          src="/image/second.png"
          alt="TV"
          class="h-full w-auto max-w-none"
        />
      </q-carousel-slide>
      <q-carousel-slide
        name="layers"
        class="relative overflow-hidden flex justify-center items-center h-full"
      >
        <img
          src="/image/third.png"
          alt="Layers"
          class="h-full w-auto max-w-none"
        />
      </q-carousel-slide>
    </q-carousel>
  </div>
</template>

<script lang="ts">
import { onMounted, onUnmounted, ref } from "vue";

export default {
  setup() {
    const slide = ref("style");
    const slides = ref(["style", "tv", "layers"]);
    let intervalId: any;

    const advanceSlide = () => {
      const currentIndex = slides.value.indexOf(slide.value);
      const nextIndex = (currentIndex + 1) % slides.value.length;
      slide.value = slides.value[nextIndex];
    };

    onMounted(() => (intervalId = setInterval(advanceSlide, 3000)));

    onUnmounted(() => clearInterval(intervalId));

    return { slide };
  },
};
</script>

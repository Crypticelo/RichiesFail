<script setup lang="ts">
let intervalId: NodeJS.Timeout;
const slide = ref("1.png");
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
  <q-carousel
    v-model="slide"
    transition-prev="slide-right"
    transition-next="slide-left"
    animated
    control-color="primary"
    class="rounded-lg overflow-hidden relative custom-carousel"
  >
    <q-carousel-slide
      v-for="item in slides"
      :key="item"
      :name="item"
      class="relative overflow-hidden flex justify-center items-center h-full w-full"
    >
      <img :src="'/images/' + item" class="h-full w-full object-contain" />
    </q-carousel-slide>
  </q-carousel>
  <button @click="$q.dark.toggle()">theme</button>
  <div class="text-xl text-red-500">asd</div>
</template>

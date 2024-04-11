<template>
  <Navbar></Navbar>
  <div class="q-pa-md">
    <q-carousel
      v-model="slide"
      transition-prev="slide-right"
      transition-next="slide-left"
      animated
      control-color="primary"
      class="rounded-borders custom-carousel"
    >
      <q-carousel-slide name="style" class="carousel-slide">
        <img src="/image/first.png" alt="Style" class="carousel-image" />
      </q-carousel-slide>
      <q-carousel-slide name="tv" class="carousel-slide">
        <img src="/image/second.png" alt="TV" class="carousel-image" />
      </q-carousel-slide>
      <q-carousel-slide name="layers" class="carousel-slide">
        <img src="/image/third.png" alt="Layers" class="carousel-image" />
      </q-carousel-slide>
    </q-carousel>
  </div>
</template>

<style scoped>
.custom-carousel .q-carousel-slide {
  position: relative;
  overflow: hidden;
}

.carousel-slide {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100%;
}

.carousel-image {
  width: auto; 
  max-width: none; 
  height: 100%;
}
</style>

<script lang="ts">
import { onMounted, onUnmounted, ref } from "vue";

export default {
  setup() {
    const slide = ref("style");
    const lorem = ref(
      "Lorem ipsum dolor, sit amet consectetur adipisicing elit. Itaque voluptatem totam, architecto cupiditate officia rerum, error dignissimos praesentium libero ab nemo provident incidunt ducimus iusto perferendis porro earum. Totam, numquam?"
    );

    const slides = ref(["style", "tv", "layers"]);
    let intervalId: any;

    const advanceSlide = () => {
      const currentIndex = slides.value.indexOf(slide.value);
      const nextIndex = (currentIndex + 1) % slides.value.length;
      slide.value = slides.value[nextIndex];
    };

    onMounted(() => {
      intervalId = setInterval(advanceSlide, 3000); // changes slide every 3000 milliseconds (3 seconds)
    });

    onUnmounted(() => {
      clearInterval(intervalId);
    });

    return {
      slide,
      lorem,
    };
  },
};
</script>
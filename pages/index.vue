<template>
  <div class="q-pa-md">
    <q-carousel
      v-model="slide"
      transition-prev="slide-right"
      transition-next="slide-left"
      animated
      control-color="primary"
      class="rounded-borders"
    >
      <q-carousel-slide name="style" class="column no-wrap flex-center">
        <img src="/image/first.png" alt="Style" />
      </q-carousel-slide>
      <q-carousel-slide name="tv" class="column no-wrap flex-center">
        <img src="/image/second.png" alt="TV" />
      </q-carousel-slide>
      <q-carousel-slide name="layers" class="column no-wrap flex-center">
        <img src="/image/third.png" alt="Layers" />
      </q-carousel-slide>
    </q-carousel>
  </div>
</template>

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
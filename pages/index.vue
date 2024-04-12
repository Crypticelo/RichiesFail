<script setup lang="ts">
import Layout from "~/layout/Layout.vue";
</script>

<template>
  <Layout>
    <div class="container mx-auto">
      <button @click="$q.dark.toggle()">theme</button>
      <div class="text-xl text-red-500">asd</div>
    </div>
  </Layout>
</template>

<style>
@import "tailwindcss/base";
@import "tailwindcss/components";
@import "tailwindcss/utilities";
</style>

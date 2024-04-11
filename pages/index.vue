<script setup lang="ts">
import Layout from "~/layout/Layout.vue";
</script>

<template>
  <Layout>
    <button @click="$q.dark.toggle()">theme</button>
    <div class="text-xl text-red-500">asd</div>
  </Layout>
</template>

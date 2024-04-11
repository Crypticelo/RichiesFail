<script lang="ts" setup>
const darkActive = ["body--dark"];
useQuasar().dark.set(true);
useHead({ bodyAttrs: { class: darkActive } });
</script>

<template>
  <NuxtLayout :key="darkActive.join('')">
    <NuxtPage />
  </NuxtLayout>
</template>

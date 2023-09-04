<script setup lang="ts">
import { useRoute } from 'vue-router';

const route = useRoute();
</script>

<template>
  <div>
    <template v-if="route.path !== '/'">
      <Header />
    </template>
    <NuxtPage />
    <template v-if="route.path !== '/home'">
      <Footer />
    </template>
  </div>
</template>

<style scoped>
</style>

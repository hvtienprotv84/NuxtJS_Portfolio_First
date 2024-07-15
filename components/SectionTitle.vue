<script setup lang="ts">
import { defineProps } from 'vue';

const props = defineProps<{
  title: string;
}>();
</script>

<template>
  <h1 class="text-5xl font-bold mb-6 text-center md:text-left uppercase text-white pt-5 md:pt-10" data-aos="fade-right">
    {{ title }}
  </h1>
</template>

<style scoped>
h1 {
  cursor: default;
}
</style>

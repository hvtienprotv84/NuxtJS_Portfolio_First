<script setup lang="ts">
import { defineProps } from 'vue';

const props = defineProps<{
  competence: {
    id: number;
    icon: string;
    name: string;
  };
}>();
</script>

<template>
  <div class="justify-center p-1"
       data-aos="zoom-in"
       :data-aos-delay="competence.id * 50">
    <div class="icon flex flex-col">
      <i :class="['text-6xl', competence.icon]"></i>
      <span class="text-center">{{ competence.name }}</span>
    </div>
  </div>
</template>

<style scoped>
.icon {
  z-index: 1;
  transition: all 0.2s ease-in-out;
}

.icon:hover {
  transform: scale(1.3);
  transition: 0.3s;
}
</style>

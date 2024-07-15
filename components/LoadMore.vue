<template>
  <div class="w-full">
    <div class="flex flex-wrap justify-center gap-4">
      <slot :visibleItems="displayedItems"></slot>
    </div>
    <div v-if="items.length > itemsToShow" class="flex justify-center mt-4">
      <button @click="showMoreItems" class="text-xl font-bold text-gray-700 dark:text-gray-300 hover:text-gray-900 dark:hover:text-gray-100">
        ↓ Xem Thêm
      </button>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, computed } from 'vue';

const props = defineProps({
  items: {
    type: Array,
    required: true
  },
  initialShow: {
    type: Number,
    default: 3
  },
  increment: {
    type: Number,
    default: 3
  }
});

const itemsToShow = ref(props.initialShow);

const displayedItems = computed(() => props.items.slice(0, itemsToShow.value));

const showMoreItems = () => {
  itemsToShow.value += props.increment;
};
</script>

<style scoped>
/* Ajoutez des styles si nécessaire */
</style>

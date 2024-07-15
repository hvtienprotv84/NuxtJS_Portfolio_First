<template>
  <div class="p-card mx-auto">
    <div @click="openProjectModal" class="cursor-pointer">
      <NuxtImg :src="project.image" :alt="project.title" class="max-h-[172px] max-w-[300px] object-cover object-top rounded-lg shadow-md mb-4" sizes="100vw sm:50vw md:400px"/>
      <h3 class="font-bold">{{ project.title }}</h3>
      <p>{{ truncatedDescription }}</p>
    </div>
    <UModal v-model="showProjectModal">
      <UCard :ui="{ ring: '', divide: 'divide-y divide-gray-100 dark:divide-gray-800' }">
        <template #header>
          <div class="items-end right-0">
            <UButton color="gray" variant="ghost" icon="i-heroicons-x-mark-20-solid" class="-my-1" @click="showProjectModal = false" />
          </div>
        </template>
        <div class="p-7 w-full">
          <div class="items-center justify-center">
            <NuxtImg :src="project.image" :alt="project.title" class="mx-auto h-[172px] w-[300px] object-cover object-top rounded-lg shadow-md mb-4" sizes="100vw sm:50vw md:400px"/>
            <h1 class="text-center font-bold">{{ project.title }}</h1>
          </div>
          <div class="text-left">
            <p>{{ project.description }}</p>
          </div>
          <div class="pt-5 flex flex-wrap items-center justify-center space-x-2">
            <i v-for="icon in project.technologies" :key="icon" :class="['text-4xl', icon]"></i>
          </div>
        </div>
        <template #footer>
          <div class="flex flex-wrap items-center justify-center space-x-2">
            <a v-if="project.github != null" :href="project.github" target="_blank" class="bg-green-500 p-2 rounded-[10px]"><i class="devicon-github-original p-1"></i>Repo Github</a>
            <a v-if="project.website != null" :href="project.website" target="_blank" class="bg-green-500 p-2 rounded-[10px]" ><i class="devicon-chrome-plain p-1"></i>Website</a>
          </div>
        </template>
      </UCard>
    </UModal>
  </div>
</template>

<script setup lang="ts">
import { ref, computed } from 'vue';


const props = defineProps<{
  project: {
    title: string;
    image: string;
    github: string;
    website: string;
    technologies: string[];
    description: string;
  };
}>();

const showProjectModal = ref(false);

const openProjectModal = () => {
  showProjectModal.value = true;
};

const truncatedDescription = computed(() => {
  const maxLength = 100;
  if (props.project.description.length > maxLength) {
    return props.project.description.substring(0, maxLength) + '...';
  }
  return props.project.description;
});
</script>

<style scoped>
.p-card {
  width: 300px;
  margin-right: 2rem;
  text-align: center;
  transition: all 0.2s ease-in-out;
}

.p-card:hover {
  transform: scale(1.1);
}
@media (max-width: 480px) {
  .p-card:hover {
    transform: scale(1);
  }
}

.p-card img {
  width: 100%;
  height: auto;
  border-radius: 10px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.5);
  margin-bottom: 1rem;
}

.p-card h3 {
  margin-bottom: 0.5rem;
}

.p-card p {
  margin-bottom: 1rem;
}
</style>

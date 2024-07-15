<script setup lang="ts">
import { defineProps, computed, ref } from 'vue';

const props = defineProps<{
  experience: {
    entreprise: string;
    title: string;
    logo: string;
    contract: string;
    date: string;
    description: string;
  };
}>();

const isFlipped = ref(false);
const description = props.experience.description;

const formattedDescription = computed(() => {
  return description.replace(/\n/g, '<br>');
});

function flipCard() {

  isFlipped.value = !isFlipped.value;
}
</script>

<template>
  <div data-aos="zoom-in-up" data-aos-delay="50">
    <div class="card-container">
      <div class="card" :class="{ 'card-flipped': isFlipped }" @click="flipCard">
        <div class="card-front glass-card">
          <h3 class="text-center text-xl font-bold pb-[10px]">{{ experience.title }}</h3>
          <NuxtImg v-if="experience.logo" :src="experience.logo" :alt="experience.entreprise" class="max-w-[15rem]" sizes="100vw sm:50vw md:400px"/>
          <h4 v-else class="text-lg">{{ experience.entreprise }}</h4>
          <p class="date">{{ experience.date }}</p>
          <!-- <p class="contract">{{ experience.contract }}</p> -->
        </div>
        <div class="card-back glass-card">
          <h4 class="text-center text-lg font-bold top-0">{{ experience.title }}</h4>
          <p v-html="formattedDescription" class="description  text-left"></p>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.glass-card {
  background: rgba(255, 255, 255, 0.32);
  backdrop-filter: blur(10px);
  border-radius: 10px;
  padding: 20px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  transform-style: preserve-3d;
}

.card-container {
  perspective: 1000px;
  display: flex;
  justify-content: center;
  align-items: center;
}

.card {
  width: 300px;
  height: 400px;
  position: relative;
  transform-style: preserve-3d;
  cursor: pointer;
  transition: transform 0.2s ease-in-out;
  margin: 20px;
}

.card:hover {
  transform: scale(1.1);
}
@media (max-width: 480px) {
  .card:hover {
    transform: scale(1);
  }
}

.card-front,
.card-back {
  position: absolute;
  width: 100%;
  height: 100%;
  backface-visibility: hidden;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  transform: rotateY(0deg);
  transition: transform 0.5s ease-in-out;
}

.card-back {
  transform: rotateY(180deg);
}

.card-flipped .card-front {
  transform: rotateY(180deg);
}

.card-flipped .card-back {
  transform: rotateY(360deg);
}

.date,
.contract {
  font-style: italic;
  margin-top: 0.5rem;
}

.description {
  margin-top: 1rem;
  text-align: left;
}
</style>

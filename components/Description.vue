<template>
  <UContainer class="py-12">
    <SectionTitle title="Giới Thiệu!" />
    <div class="flex flex-col md:flex-row items-center md:items-stretch pt-10 pb-20">
      <div class="hidden md:flex md:w-1/3 md:p-4 about-image  items-center justify-center" data-aos="fade-right" data-aos-duration="2000">
        <NuxtImg class="hidden md:block" :src="about.image" alt="Photo de profil" sizes="100vw sm:50vw md:400px" />
      </div>
      <div class="md:w-2/3 md:p-4 flex flex-col justify-center" data-aos="fade-left" data-aos-duration="2000">
        <div class="text-left mb-6">
          <h2 class="text-4xl md:text-7xl font-bold font-sans uppercase">{{ about.name }}</h2>
          <h3 class="text-2xl md:text-5xl font-medium text-gray-300">{{ about.title }}</h3>
        </div>
        <p class="text-white text-lg leading-relaxed">{{ about.description }}</p>
      </div>
    </div>
  </UContainer>
</template>

<script setup>
import SectionTitle from "~/components/SectionTitle.vue";
import aboutme from "~/data/aboutme.json";

const about = aboutme;
</script>

<style scoped>
.about-image {
  display: flex;
  justify-content: center;
  align-items: center;
}

.about-image img {
  width: 100%;
  max-width: 20rem;
  height: auto;
  border-radius: 69% 31% 27% 73% / 45% 49% 51% 55%;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.5);
}
</style>

<script setup lang="ts">
import SectionTitle from "~/components/SectionTitle.vue";
import ExperienceCard from "~/components/ExperienceCard.vue";
import LoadMore from "~/components/LoadMore.vue";
import experiences from "~/data/experiences.json";
import formations from "~/data/formations.json";

const experiences_list = experiences.experiences;
// const formations_list = formations.formations;



</script>

<template>
  <UContainer class="pb-10">
    <SectionTitle title="Kinh Nghiệm"/>
    <LoadMore :items="experiences_list" :initialShow="3" :increment="3">
      <template #default="{ visibleItems }">
        <div v-for="experience in visibleItems" :key="experience.id" class="project-cards" data-aos="fade-up">
          <ExperienceCard :experience="experience" />
        </div>
      </template>
    </LoadMore>
    <!-- <SectionTitle title="Formations"/>
    <LoadMore :items="formations_list" :initialShow="3" :increment="3">
      <template #default="{ visibleItems }">
        <div v-for="formation in visibleItems" :key="formation.id" class="project-cards" data-aos="fade-up">
          <ExperienceCard :experience="formation" />
        </div>
      </template>
    </LoadMore> -->
  </UContainer>
</template>

<style scoped>

</style>
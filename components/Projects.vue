<template>
  <UContainer>
    <SectionTitle title="Projects" />
    <LoadMore :items="projects" :initialShow="3" :increment="3">
      <template #default="{ visibleItems }">
        <div v-for="project in visibleItems" :key="project.id" class="project-cards" data-aos="fade-up">
          <ProjectCard :project="project" />
        </div>
      </template>
    </LoadMore>
  </UContainer>
</template>

<script setup lang="ts">
import SectionTitle from '~/components/SectionTitle.vue';
import ProjectCard from '~/components/ProjectCard.vue';
import LoadMore from '~/components/LoadMore.vue';

import project_list from '~/data/projects.json';

const projects = project_list.projects;
</script>

<style scoped>
.project-cards {
  width: 100%;
  max-width: 300px;
  margin-top: 3rem;
}
</style>

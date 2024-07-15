<script setup lang="ts">
import { ref, onMounted } from 'vue';
import SectionTitle from '~/components/SectionTitle.vue';
import CompetencesIcons from './CompetencesIcons.vue';
import competences from '~/data/competences.json';

const competencesList = competences.competences;

</script>

<template>
  <UContainer>
    <SectionTitle title="Kỹ Năng" />
    <div class="grid grid-cols-3 md:grid-cols-8 gap-4 align-middle items-center pb-10 md:p-0">
      <div v-for="competence in competencesList" :key="competence.id" class="flex flex-col items-center justify-center">
        <CompetencesIcons :competence="competence"/>
      </div>
    </div>
  </UContainer>
</template>

<style scoped>
</style>

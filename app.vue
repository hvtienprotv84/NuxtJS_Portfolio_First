<template>
  <div @mousemove="handleMouseMove" class="main-container">
    <link rel="stylesheet" type='text/css' href="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/devicon.min.css" />
    <SpeedInsights />
    <Navbar></Navbar>
    <div>
      <Description id="whoami"></Description>
      <Competences id="competences"></Competences>
      <Projects id="projects"></Projects>
      <Experiences id="experiences"></Experiences>
    </div>
    <Footer></Footer>
  </div>
</template>


<script>
import { ref, onMounted, onBeforeUnmount } from 'vue';
import Description from './components/Description.vue';
import Navbar from '~/components/Navbar.vue';
import Competences from '~/components/Competences.vue';
import Experiences from '~/components/Experiences.vue';
import Footer from '~/components/Footer.vue';
import Projects from '~/components/Projects.vue';
import { SpeedInsights } from "@vercel/speed-insights/nuxt";

export default {
  setup() {
    useHead({
      title: 'Huỳnh Vĩnh Tiến - First NuxtJS',
      link: { rel: 'icon', type: 'image/x-icon', href: 'https://i.imgur.com/XOvWV1c.png' },
      htmlAttrs: {
        lang: 'fr'
      },
      meta: [
        { name: 'description', content: 'Samuel BLARD est un développeur Fullstack spécialiser dans le développement VueJS, ReactJS et NodeJS' }
      ]
    })
    const mainContainer = ref(null);

    const handleMouseMove = (event) => {
      // Vérification si l'appareil est mobile (largeur <= 768px)
      if (window.matchMedia('(max-width: 768px)').matches) {
        return; // Ne rien faire si c'est un appareil mobile
      }

      const { clientX, clientY } = event;
      const { innerWidth, scrollY } = window;

      const xPercent = (clientX / innerWidth) * 100;
      const yPercent = ((clientY + scrollY) / document.documentElement.scrollHeight) * 100;

      if (mainContainer.value) {
        mainContainer.value.style.setProperty('--mouse-x', `${xPercent}%`);
        mainContainer.value.style.setProperty('--mouse-y', `${yPercent}%`);
      }
    };

    onMounted(() => {
      mainContainer.value = document.querySelector('.main-container');
    });

    onBeforeUnmount(() => {
      mainContainer.value = null;
    });

    return {
      handleMouseMove,
    };
  },
  components: {
    Description,
    Navbar,
    Competences,
    Experiences,
  },
};
</script>


<style scoped>
.main-container {
  min-height: 100vh;
  background: radial-gradient(circle at var(--mouse-x) var(--mouse-y), rgba(101, 255, 133, 0.66), rgba(14, 120, 0, 0.21) 20%);
  transition: background 0.2s;
}

@media (max-width: 768px) {
  .main-container {
    background: rgba(14, 120, 0, 0.21); /* Retire le radial-gradient pour les appareils mobiles */
  }
}
</style>

<style>
:root {
  --mouse-x: 50%;
  --mouse-y: 50%;
}

html {
  scroll-behavior: smooth;
}

body {
  background: #000000;
  margin: 0;
  padding: 0;
}
</style>

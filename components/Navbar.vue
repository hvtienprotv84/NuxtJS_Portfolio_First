<template>
  <nav
      :class="['navbar flex items-center justify-between w-full h-20 px-4 bg-white dark:bg-[#000000b3] text-gray-800 dark:text-white sticky top-0 transition-all duration-150']"
  >
    <div>
      <a href="/">
        <img class="w-[70px] h-[60px] mt-[-3px] sm:ml-[50px]"src="../public/logo_1.png"/>
      </a>
    </div>

    <ul class="flex flex-row font-bold text-[10px] sm:text-2xl">
      <a href="#whoami">
        <li>Giới Thiệu</li>
      </a>
      <a href="#competences">
        <li class="sm:ml-[100px] ml-[10px] ">Kỹ Năng</li>
      </a>
      <a href="#projects">
        <li class="sm:ml-[100px] ml-[10px]">Projects</li>
      </a>
      <a href="#experiences">
        <li class="sm:ml-[100px] ml-[10px]">Kinh Nghiệm</li>
      </a>
    </ul>

    <div class="relative">
      <button title="Menu" @click="toggleMenu" class="focus:outline-none">
        <svg
            class="w-6 h-6"
            fill="none"
            stroke="currentColor"
            viewBox="0 0 24 24"
            xmlns="http://www.w3.org/2000/svg"
        >
          <path
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M4 6h16M4 12h16m-7 6h7"
          ></path>
        </svg>
      </button>

      <div v-if="isMenuOpen" class="absolute right-0 mt-2 w-48 bg-white dark:bg-gray-700 rounded-md shadow-lg z-50">
        <ul>
          <li class="border-b border-gray-200 dark:border-gray-600">
            <a href="#whoami" class="block px-4 py-2 text-sm">
              Giới Thiệu
            </a>
          </li>
          <li class="border-b border-gray-200 dark:border-gray-600">
            <a href="#competences" class="block px-4 py-2 text-sm">
              Kỹ Năng
            </a>
          </li>
          <li class="border-b border-gray-200 dark:border-gray-600">
            <a href="#projects" class="block px-4 py-2 text-sm">
              Projects
            </a>
          </li>
          <li>
            <a href="#experiences" class="block px-4 py-2 text-sm">
              Kinh Nghiệm
            </a>
          </li>
        </ul>
      </div>
    </div>
  </nav>
</template>

<script>
export default {
  data() {
    return {
      isMenuOpen: false,
    };
  },
  methods: {
    toggleMenu() {
      this.isMenuOpen = !this.isMenuOpen;
    }
  },
  watch: {
    isMenuOpen(newVal) {
      if (newVal) {
        document.addEventListener('click', this.closeMenu);
      } else {
        document.removeEventListener('click', this.closeMenu);
      }
    },
  },
  methods: {
    toggleMenu() {
      this.isMenuOpen = !this.isMenuOpen;
    },
    closeMenu(event) {
      if (!this.$el.contains(event.target)) {
        this.isMenuOpen = false;
      }
    }
  },
  beforeDestroy() {
    document.removeEventListener('click', this.closeMenu);
  },
};
</script>

<style scoped>
.navbar {
  z-index: 999;
}
</style>

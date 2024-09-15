<template>
  <div :class="theme" class="transition-all duration-500">
    <div class="section navbar px-2 lg:px-80 mx-auto bg-gray-100 text-gray-900 dark:bg-black dark:bg-opacity-95 dark:text-gray-100 transition-all duration-500">
      <div class="navbar-start">
        <a class="btn btn-ghost text-xl">
          <img v-if="theme === 'dark'" src="../images/logo.png" class="h-8 transition-all duration-500" alt="Logo">
          <img v-else src="../images/logo2.png" class="h-8 transition-all duration-500" alt="Logo">
        </a>
      </div>
      <div class="navbar-center hidden lg:flex">
        <ul class="menu menu-horizontal px-1">
          <li><a @click.prevent="scrollToSection('home')" class="hover:bg-gray-300 hover:text-gray-600 rounded-3xl text-md">Home</a></li>
          <li><a @click.prevent="scrollToSection('services')" class="hover:bg-gray-300 hover:text-gray-600 rounded-3xl text-md">Services</a></li>
          <li><a @click.prevent="scrollToSection('pricing')" class="hover:bg-gray-300 hover:text-gray-600 rounded-3xl text-md">Pricing</a></li>
          <li><a @click.prevent="scrollToSection('contact')" class="hover:bg-gray-300 hover:text-gray-600 rounded-3xl text-md">ContactUs</a></li>

        </ul>
      </div>

      <div class="navbar-end">
        <!-- Theme Toggle Button -->
        <button class="mr-8 mt-2" @click="toggleTheme">
          <i v-if="theme === 'dark'" class="fa-regular fa-sun text-yellow-400"></i>
          <i v-else class="fa-solid fa-moon"></i>
        </button>

        <button class="relative inline-flex items-center justify-center p-0.5 shadow-md shadow-pink-500 overflow-hidden text-sm font-medium rounded-3xl group bg-gradient-to-br from-pink-500 to-orange-400 group-hover:from-pink-500 group-hover:to-orange-400 hover:text-white focus:ring-4 focus:outline-none focus:ring-pink-200 dark:focus:ring-pink-800">
          <span class="relative px-5 py-2 transition-all font-bold ease-in duration-75 bg-white dark:bg-gray-900 rounded-3xl group-hover:bg-opacity-0">
            Buy Now
          </span>
        </button>

        <!-- Hamburger Menu for Small Screens -->
        <button class="lg:hidden mx-4" @click="toggleMenu">
          <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16m-7 6h7" />
          </svg>
        </button>
      </div>
    </div>

    <!-- Aside for Small Screens Menu -->
    <aside class="aside-menu fixed inset-y-0 left-0 w-full bg-gray-100 text-gray-900 dark:bg-black dark:bg-opacity-95 dark:text-gray-100 z-40 transform transition-transform duration-300 ease-in-out" :class="{ 'translate-x-0': menuOpen, '-translate-x-full': !menuOpen }">
      <div class="p-4 flex mx-auto justify-center align-middle text-center relative top-60">
        <ul class="menu menu-vertical w-full text-center justify-center">
          <li><a @click.prevent="scrollToSection('home')" class=" hover:bg-gray-300 hover:text-gray-600 rounded-3xl w-full text-center justify-center text-3xl">Home</a></li>
          <li><a @click.prevent="scrollToSection('services')" class="hover:bg-gray-300 hover:text-gray-600 rounded-3xl w-full text-center justify-center text-3xl">Services</a></li>
          <li><a @click.prevent="scrollToSection('pricing')" class="hover:bg-gray-300 hover:text-gray-600 rounded-3xl w-full text-center justify-center text-3xl">Pricing</a></li>
          <li><a @click.prevent="scrollToSection('contact')" class="hover:bg-gray-300 hover:text-gray-600 rounded-3xl w-full text-center justify-center text-3xl">ContactUs</a></li>


        </ul>
      </div>
      <!-- Close Button -->
      <button class="absolute top-4 right-4 p-2 rounded-full hover:bg-gray-600" @click="toggleMenu">
        <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
        </svg>
      </button>
    </aside>


  </div>
</template>

<script>
export default {
  data() {
    return {
      menuOpen: false, // State to track menu visibility
      theme: 'dark' // State to track the current theme
    };
  },
  methods: {
    toggleMenu() {
      this.menuOpen = !this.menuOpen; // Toggle the menu state
    },
    toggleTheme() {
  this.theme = this.theme === 'dark' ? 'light' : 'dark'; // Toggle between dark and light mode
  document.documentElement.classList.toggle('dark', this.theme === 'dark');
  localStorage.setItem('theme', this.theme); // Save theme preference in localStorage
},

    scrollToSection(sectionId) {
      const section = document.getElementById(sectionId);
      section.scrollIntoView({ behavior: 'smooth' }); // Smooth scroll to section
    }
  },
  mounted() {
    // Check localStorage for a saved theme preference
    const savedTheme = localStorage.getItem('theme');
    if (savedTheme) {
      this.theme = savedTheme;
    } else {
      const userPrefersDark = window.matchMedia('(prefers-color-scheme: dark)').matches;
      this.theme = userPrefersDark ? 'dark' : 'light';
    }
    document.documentElement.classList.toggle('dark', this.theme === 'dark');
  }
};
</script>

<style>
/* Smooth transition for theme change */
.transition-all {
  transition: background-color 0.5s ease, color 0.5s ease;
}

/* Smooth transition for aside menu */
.aside-menu {
  transition: transform 0.3s ease-in-out;
}
</style>

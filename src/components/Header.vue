<template>
  <header ref="header">
    <nav class="container mx-auto px-3 py-3 mb-3">
      <div class="flex items-start justify-between">
        <!-- Name and tagline container -->
        <div class="flex flex-col">
          <div class=" text-xl font-bold leading-tight text-lime-400">Information</div>
        </div>

        <!-- Desktop Navigation Links -->
        <div class="hidden md:flex space-x-6 pt-1">
          <a
            v-for="item in navItems"
            :key="item.id"
            :href="item.href"
            @click="smoothScroll"
            class="relative text-white text-lg font-bold transition-all duration-300 ease-in-out hover:text-lime-400 hover:scale-105 after:content-[''] after:absolute after:left-0 after:-bottom-1 after:w-0 after:h-0.5 after:bg-lime-400 hover:after:w-full after:transition-all after:duration-300"
          >
            {{ item.text }}
          </a>
        </div>

        <!-- Hamburger Icon -->
        <button
          @click="toggleMenu"
          class="md:hidden focus:outline-none pt-1 active:scale-95 transition-transform duration-150"
        >
          <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path
              v-if="!menuOpen"
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M4 6h16M4 12h16M4 18h16"
            />
            <path
              v-else
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M6 18L18 6M6 6l12 12"
            />
          </svg>
        </button>
      </div>

      <!-- Mobile Menu -->
      <transition name="fade-slide">
        <div v-if="menuOpen" class="md:hidden mt-4 pb-4">
          <div class="flex flex-col space-y-3 bg-white shadow-md rounded-lg p-4 border border-gray-100">
            <a
              v-for="item in navItems"
              :key="item.id"
              :href="item.href"
              @click="closeMenu"
              class="text-gray-800  transition py-2 px-2 rounded hover:bg-gray-100 hover:text-lime-400  hover:scale-105 active:scale-95 transform duration-200"
            >
              {{ item.text }}
            </a>
          </div>
        </div>
      </transition>
    </nav>
  </header>
</template>

<script>
export default {
  data() {
    return {
      menuOpen: false,
      navItems: [
        { id: 1, text: 'Profile', href: '#profile' },
        { id: 2, text: 'Skills', href: '#skills' },
        { id: 3, text: 'Projects', href: '#projects' },
        { id: 4, text: 'Education', href: '#education' },
        { id: 5, text: 'Contact', href: '#social' }
      ]
    }
  },
  methods: {
    toggleMenu() {
      this.menuOpen = !this.menuOpen;
    },
    closeMenu() {
      this.menuOpen = false;
    },
    smoothScroll(event) {
      // Optionally implement smooth scrolling here
    }
  }
}
</script>

<style scoped>
.fade-slide-enter-active,
.fade-slide-leave-active {
  transition: all 0.3s ease;
}
.fade-slide-enter-from,
.fade-slide-leave-to {
  opacity: 0;
  transform: translateY(-10px);
}
</style>

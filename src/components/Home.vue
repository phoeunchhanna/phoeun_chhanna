<template>
  <div class=" bg-zinc-900 font-sans overflow-hidden relative">
    <!-- Animated background elements -->
    <div class="absolute inset-0 overflow-hidden">
      <div class="absolute top-0 left-0 w-full h-full bg-grid-pattern opacity-5"></div>
      <div v-for="i in 8" :key="i" class="absolute rounded-full bg-lime-400 opacity-10" :class="`circle-${i}`" :style="{
        width: `${Math.random() * 200 + 50}px`,
        height: `${Math.random() * 200 + 50}px`,
        left: `${Math.random() * 100}%`,
        top: `${Math.random() * 100}%`,
        filter: 'blur(40px)'
      }"></div>
    </div>

    <!-- Main content container -->
    <div class="relative z-10 container mx-auto px-4 sm:px-6 lg:px-8 py-12">
      <!-- Header/Navigation -->
      <header class="flex justify-between items-center mb-16 animate-fade-in">
        <!-- Logo -->
        <h1 class="text-2xl font-bold text-white">
          <span class="text-lime-400">PC</span>Code
        </h1>

        <!-- Social Icons -->
        <div class="flex gap-4">
          <a v-for="(social, index) in socialLinks" :key="index" :href="social.url" target="_blank"
            rel="noopener noreferrer" :aria-label="social.name"
            class="p-3 bg-lime-300 rounded-full hover:bg-lime-400 hover:text-zinc-900 transition-all duration-300 transform hover:-translate-y-1"
            :class="`animate-bounce-in delay-${index + 1}`">
            <i :class="social.icon"></i>
          </a>
        </div>
      </header>

      <!-- Hero Section -->
      <main class="flex flex-col lg:flex-row items-center gap-12">
        <!-- Profile Image (Left) -->
        <div class="w-full lg:w-1/3 flex justify-center animate-slide-in-left">
          <div class="relative group">
            <img src="@/assets/image/photo_1_2025-05-22_22-45-12.jpg" alt="Phoeun Chhanna"
              class="w-64 h-64 sm:w-80 sm:h-80 rounded-full object-cover border-4 border-lime-400 shadow-lg transform transition duration-500 group-hover:scale-105 group-hover:shadow-xl" />
            <div
              class="absolute inset-0 rounded-full border-4 border-transparent group-hover:border-white transition-all duration-500">
            </div>
            <div
              class="absolute -bottom-6 left-1/2 transform -translate-x-1/2 bg-zinc-800 px-6 py-2 rounded-full shadow-md">
              <p class="text-white font-medium">Phoeun Chhanna</p>
            </div>
          </div>
        </div>

        <!-- Content (Right) -->
        <div class="w-full lg:w-2/3 animate-slide-in-right">
          <!-- Intro Text -->
          <div class="mb-8">
            <h1 class="text-4xl sm:text-5xl md:text-6xl font-bold text-white leading-tight mb-4">
              Hello, I'm <span class="text-lime-400 animate-pulse">Phouen Chhanna</span>
            </h1>
            <h2 class="text-2xl sm:text-3xl text-gray-300 mb-6">
              Nickname <span class="text-red-400 font-bold">Chhanna Code</span>
            </h2>
            <p class="text-xl text-gray-400 mb-8">
              <span class="text-blue-300 font-medium">Web Developer</span> and
              <span class="text-blue-300 font-medium">Content Creator</span> based in Cambodia
            </p>
          </div>

          <!-- Stats -->
          <div class="flex flex-wrap gap-8 mb-10">
            <div v-for="(stat, index) in stats" :key="index"
              class="bg-zinc-800 p-6 rounded-xl shadow-md transform transition duration-500 hover:scale-105 hover:bg-zinc-700"
              :class="`animate-stats-in delay-${index + 1}`">
              <p class="text-4xl font-bold text-lime-400">{{ stat.value }}</p>
              <p class="text-sm text-gray-400">{{ stat.label }}</p>
            </div>
          </div>

          <!-- CTA Button -->
          <a href="/Phoeun_Chhanna_CV.pdf" download="phoeunchhanna.pdf" class="inline-block">
            <button
              class="relative overflow-hidden group bg-lime-400 text-zinc-900 px-8 py-4 rounded-full font-bold text-lg shadow-lg transform transition duration-500 hover:scale-105 hover:shadow-xl animate-fade-in-up">
              <span class="relative z-10">Download CV</span>
              <div class="absolute inset-0 bg-white opacity-0 group-hover:opacity-20 transition duration-300"></div>
            </button>
          </a>
        </div>
      </main>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HomePage',
  data() {
    return {
      socialLinks: [
        { name: 'Telegram', url: 'https://t.me/Chhanna_phoeun', icon: 'fab fa-telegram' },
        { name: 'GitHub', url: 'https://github.com/dashboard', icon: 'fab fa-github' },
        { name: 'LinkedIn', url: 'https://www.linkedin.com/in/chhanna-phoeun-6a4668257/', icon: 'fab fa-linkedin' },
        { name: 'YouTube', url: 'https://www.youtube.com/@ChhannaCode2002', icon: 'fab fa-youtube' }
      ],
      stats: [
        { value: '1+', label: 'Years of Experience' },
        { value: '5+', label: 'Happy Clients' }
      ]
    }
  }
}
</script>

<style scoped>
@import url('https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css');

/* Background pattern */
.bg-grid-pattern {
  background-image:
    linear-gradient(to right, rgba(255, 255, 255, 0.03) 1px, transparent 1px),
    linear-gradient(to bottom, rgba(255, 255, 255, 0.03) 1px, transparent 1px);
  background-size: 40px 40px;
}

/* Animations */
.animate-fade-in {
  animation: fadeIn 1s ease-out forwards;
}

.animate-bounce-in {
  animation: bounceIn 0.6s cubic-bezier(0.175, 0.885, 0.32, 1.275) forwards;
}

.animate-slide-in-left {
  animation: slideInLeft 0.8s ease-out forwards;
}

.animate-slide-in-right {
  animation: slideInRight 0.8s ease-out forwards;
}

.animate-stats-in {
  animation: statsIn 0.6s ease-out forwards;
}

.animate-fade-in-up {
  animation: fadeInUp 0.8s ease-out forwards;
}

.delay-1 {
  animation-delay: 0.1s;
}

.delay-2 {
  animation-delay: 0.2s;
}

.delay-3 {
  animation-delay: 0.3s;
}

.delay-4 {
  animation-delay: 0.4s;
}

@keyframes fadeIn {
  from {
    opacity: 0;
  }

  to {
    opacity: 1;
  }
}

@keyframes bounceIn {
  0% {
    transform: scale(0.8);
    opacity: 0;
  }

  50% {
    transform: scale(1.1);
  }

  100% {
    transform: scale(1);
    opacity: 1;
  }
}

@keyframes slideInLeft {
  from {
    transform: translateX(-50px);
    opacity: 0;
  }

  to {
    transform: translateX(0);
    opacity: 1;
  }
}

@keyframes slideInRight {
  from {
    transform: translateX(50px);
    opacity: 0;
  }

  to {
    transform: translateX(0);
    opacity: 1;
  }
}

@keyframes statsIn {
  from {
    transform: translateY(20px);
    opacity: 0;
  }

  to {
    transform: translateY(0);
    opacity: 1;
  }
}

@keyframes fadeInUp {
  from {
    transform: translateY(20px);
    opacity: 0;
  }

  to {
    transform: translateY(0);
    opacity: 1;
  }
}

/* Circle animations */
.circle-1 {
  animation: float 15s infinite ease-in-out;
}

.circle-2 {
  animation: float 18s infinite ease-in-out reverse;
}

.circle-3 {
  animation: float 12s infinite ease-in-out;
}

.circle-4 {
  animation: float 20s infinite ease-in-out reverse;
}

.circle-5 {
  animation: float 16s infinite ease-in-out;
}

.circle-6 {
  animation: float 14s infinite ease-in-out reverse;
}

.circle-7 {
  animation: float 19s infinite ease-in-out;
}

.circle-8 {
  animation: float 13s infinite ease-in-out reverse;
}

@keyframes float {

  0%,
  100% {
    transform: translate(0, 0);
  }

  25% {
    transform: translate(10px, 10px);
  }

  50% {
    transform: translate(20px, -10px);
  }

  75% {
    transform: translate(-10px, 20px);
  }
}
</style>
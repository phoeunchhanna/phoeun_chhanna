<template>
  <section id="profile" class="px-4 py-12 sm:px-6 lg:px-8">
    <div class="mx-auto max-w-7xl">
      <div
        class="grid grid-cols-1 md:grid-cols-2 items-center gap-8 container mx-auto py-16 px-4 sm:px-6 lg:px-8">
        
        <!-- Left Column: Text Content -->
        <div class="max-w-lg text-white bg-[rgba(59,130,246,0.05)] p-5 rounded-lg shadow-md">
          <h2 class="text-3xl font-extrabold sm:text-4xl text-lime-400">About Me</h2>
          <p class="mt-4 text-lg">I graduated with a Bachelor's degree in IT. During my studies,</p>
          <p>
            Worked as a
            <span class="text-lime-200">freelancer Web Developer and System Developer</span>.
          </p>
          <p>I also participated in the creation of many websites with my classmates.</p>
          <p>
            In addition, I am a content creator on social media, which you can follow on YouTube:
            <a href="https://www.youtube.com/@ChhannaCode2002" class="text-blue-400" target="_blank">
              Chhanna Code
            </a>.
          </p>

          <hr class="border-t-2 mt-5 border-lime-500 w-72 mx-auto mb-6 animate-expand" />

          <div class="mt-2 space-y-2 text-base">
            <p class="flex items-center">
              <svg class="w-5 h-5 mr-2 text-lime-400" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                  d="M5.121 17.804A13.94 13.94 0 0112 15c2.418 0 4.677.573 6.879 1.589M15 10a3 3 0 11-6 0 3 3 0 016 0z" />
              </svg>
              Name: Phoeun Chhanna
            </p>
            <p class="flex items-center">
              <svg class="w-5 h-5 mr-2 text-lime-400" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                  d="M12 8c-1.657 0-3 1.343-3 3 0 2.25 3 6 3 6s3-3.75 3-6c0-1.657-1.343-3-3-3z" />
              </svg>
              Age: 23
            </p>
            <p class="flex items-center">
              <svg class="w-5 h-5 mr-2 text-lime-400" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                  d="M3 5h2l3 9 4-8 4 8 3-6h2" />
              </svg>
              Tel: 0883140332
            </p>
            <p class="flex items-center">
              <svg class="w-5 h-5 mr-2 text-lime-400" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                  d="M16 12H8m0 0l4-4m-4 4l4 4" />
              </svg>
              Email: phoeun.chhanna32@gmail.com
            </p>
            <p class="flex items-center">
              <svg class="w-5 h-5 mr-2 text-lime-400" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                  d="M17.657 16.657L13 12l-4.657 4.657M13 12l-4.657-4.657" />
              </svg>
              Location: Phnom Penh Thmey Sangkat, Phnom Penh, Cambodia
            </p>
          </div>
        </div>

        <!-- Right Column: Image with Tailwind Transition -->
        <div class="flex justify-center ">
          <img
            src="@/assets/image/profile.jpg"
            alt="About Us Image"
            class="w-full max-w-xs h-auto object-cover rounded-lg  transition-all duration-700 ease-in-out opacity-0 animate-fade-in shadow-lg shadow-blue-500/50"
          />
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
// No need for script when not using motion
</script>

<style scoped>
@keyframes fade-in {
  from {
    opacity: 0;
    transform: scale(0.95);
  }
  to {
    opacity: 1;
    transform: scale(1);
  }
}

.animate-fade-in {
  animation: fade-in 0.7s ease-out forwards;
  animation-delay: 0.3s;
}
</style>

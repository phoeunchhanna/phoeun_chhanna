<template lang="">
    <section class="bg-gray-100 py-12">
    <div class="max-w-6xl mx-auto px-4">
      <h2 class="text-3xl font-bold text-center text-gray-800 mb-10">Skill Projects </h2>
      
      <div class="grid gap-8 md:grid-cols-2 lg:grid-cols-3">
        <div 
          v-for="(skill, index) in skills" 
          :key="skill.title"
          class="bg-white p-6 rounded-2xl shadow-md transform hover:scale-105 transition duration-300 animate-fade-in"
          :class="`delay-${index * 100}`"
        >
          <h3 class="text-xl font-semibold mb-2" :class="`text-${skill.color}-600`">{{ skill.title }}</h3>
          <p class="text-gray-600">{{ skill.description }}</p>
        </div>
      </div>
    </div>
  </section>
</template>
<script>
export default {
     data() {
    return {
      skills: [
        {
          title: 'React.js',
          description: 'Building dynamic user interfaces with reusable components and hooks.',
          color: 'blue'
        },
        {
          title: 'Node.js & Express',
          description: 'Creating fast and scalable backend APIs with RESTful architecture.',
          color: 'green'
        },
        {
          title: 'MySQL',
          description: 'Designing and managing relational databases for web applications.',
          color: 'yellow'
        },
        {
          title: 'Tailwind CSS',
          description: 'Crafting beautiful, responsive designs using utility-first classes.',
          color: 'pink'
        },
        {
          title: 'Git & GitHub',
          description: 'Version control and team collaboration with Git best practices.',
          color: 'purple'
        },
        {
          title: 'Problem Solving',
          description: 'Strong ability to debug, optimize code, and solve real-world problems.',
          color: 'red'
        }
      ]
    }
  }
}
</script>
<style scoped>
  @keyframes fade-in {
    0% {
      opacity: 0;
      transform: translateY(20px);
    }
    100% {
      opacity: 1;
      transform: translateY(0);
    }
  }

  .animate-fade-in {
    animation: fade-in 0.6s ease-out both;
  }

  .delay-100 { animation-delay: 0.1s; }
  .delay-200 { animation-delay: 0.2s; }
  .delay-300 { animation-delay: 0.3s; }
  .delay-400 { animation-delay: 0.4s; }
  .delay-500 { animation-delay: 0.5s; }
</style>
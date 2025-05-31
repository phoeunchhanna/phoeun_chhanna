<template>
  <section id="skills" class="px-4 py-12 sm:px-6 lg:px-8">
    <div class="mx-auto max-w-7xl">
      <!-- Main Title -->
      <h2 class="text-3xl font-bold text-center mb-10 text-lime-500 animate-fade-in">My Skills</h2>

      <!-- Frontend Skills -->
      <div class="mb-10" is="p" preset="slideVisibleLeft">
        <h2 class="text-3xl font-bold text-center mb-3 text-lime-500 animate-fade-in delay-100">Frontend Web Development
        </h2>
        <hr class="border-t-2 border-lime-500 w-48 mx-auto mb-6 animate-expand" />
        <div class="max-w-5xl mx-auto grid grid-cols-2 sm:grid-cols-3 md:grid-cols-5 gap-6">
          <div v-for="(skill, index) in allSkills" :key="skill.name"
            class="bg-gray-200 text-center py-6 px-4 rounded-lg shadow-lg hover:shadow-xl transition-all duration-300 transform hover:-translate-y-2 hover:bg-lime-200 hover:text-zinc-900 group"
            :class="`animate-card-in delay-${index * 100}`">
            <a :href="skill.link" target="_blank" rel="noopener noreferrer" class="block">
              <img :src="skill.logo" :alt="skill.name"
                class="h-12 mx-auto mb-4 transition-all shadow-lg duration-300 group-hover:scale-110 group-hover:rotate-3" />
              <p class="text-sm font-semibold text-blue-500  group-hover:text-zinc-900 transition-colors duration-300">
                {{ skill.name }}
              </p>
            </a>
          </div>
        </div>
      </div>

      <!-- Backend Skills -->
      <div class="mb-10" is="p" preset="slideVisibleLeft">
        <h2 class="text-3xl font-bold text-center mb-3 text-lime-500 animate-fade-in delay-200">Backend Web Development
        </h2>
        <hr class="border-t-2 border-lime-500 w-48 mx-auto mb-6 animate-expand delay-300" />
        <div class="max-w-5xl mx-auto grid grid-cols-2 sm:grid-cols-3 md:grid-cols-5 gap-6">
          <div v-for="(skill, index) in backend" :key="skill.name"
            class="bg-gray-200 text-center py-6 px-4 rounded-lg shadow-lg hover:shadow-xl transition-all duration-300 transform hover:-translate-y-2 hover:bg-lime-200 hover:text-zinc-900 group"
            :class="`animate-card-in delay-${index * 100 + 300}`">
            <a :href="skill.link" target="_blank" rel="noopener noreferrer" class="block">
              <img :src="skill.logo" :alt="skill.name"
                class="h-12 mx-auto mb-4 transition-all duration-300 group-hover:scale-110 group-hover:-rotate-3" />
              <p class="text-sm font-semibold text-blue-500  group-hover:text-zinc-900 transition-colors duration-300">
                {{ skill.name }}
              </p>
            </a>
          </div>
        </div>
      </div>

      <!-- Other Skills -->
      <div>
        <h2 class="text-3xl font-bold text-center mb-3 text-lime-500 animate-fade-in delay-400">Other Skills</h2>
        <hr class="border-t-2 border-lime-500 w-48 mx-auto mb-6 animate-expand delay-500" />
        <div class="max-w-5xl mx-auto grid grid-cols-2 sm:grid-cols-3 md:grid-cols-5 gap-6">
          <div v-for="(skill, index) in other" :key="skill.name"
            class="bg-gray-200 text-center py-6 px-4 rounded-lg shadow-lg hover:shadow-xl transition-all duration-300 transform hover:-translate-y-2 hover:bg-lime-200 hover:text-zinc-900 group"
            :class="`animate-card-in delay-${index * 100 + 500}`">
            <a :href="skill.link" target="_blank" rel="noopener noreferrer" class="block">
              <img :src="skill.logo" :alt="skill.name"
                class="h-12 mx-auto mb-4 transition-all duration-300 group-hover:scale-110 group-hover:rotate-6" />
              <p class="text-sm font-semibold text-blue-500 group-hover:text-zinc-900 transition-colors duration-300">
                {{ skill.name }}
              </p>
            </a>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'Skills',
  data() {
    return {
      allSkills: [
        {
          name: 'React',
          logo: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/react/react-original.svg',
          link: 'https://reactjs.org/'
        },
        {
          name: 'Vue',
          logo: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/vuejs/vuejs-original.svg',
          link: 'https://vuejs.org/'
        },
        {
          name: 'Tailwind',
          logo: 'https://th.bing.com/th/id/OIP.4j7LvA999TgVzlsDg_Uu7AHaEx?cb=iwp2&rs=1&pid=ImgDetMain',
          link: 'https://tailwindcss.com/'
        },
        {
          name: 'Bootstrap',
          logo: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/bootstrap/bootstrap-original.svg',
          link: 'https://getbootstrap.com/'
        },
        {
          name: 'CSS',
          logo: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/css3/css3-original.svg',
          link: 'https://developer.mozilla.org/en-US/docs/Web/CSS'
        },
      ],
      backend: [
        {
          name: 'Laravel',
          logo: 'https://th.bing.com/th/id/OIP.s7ZEqkmVrugV-4MdcVxMaAHaHa?cb=iwp2&rs=1&pid=ImgDetMain',
          link: 'https://laravel.com/'
        },
        {
          name: 'C#',
          logo: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/csharp/csharp-original.svg',
          link: 'https://learn.microsoft.com/en-us/dotnet/csharp/'
        },
        {
          name: 'ASP.NET',
          logo: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/dot-net/dot-net-original.svg',
          link: 'https://dotnet.microsoft.com/en-us/apps/aspnet'
        },
        {
          name: 'SQL Server',
          logo: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/microsoftsqlserver/microsoftsqlserver-plain.svg',
          link: 'https://www.microsoft.com/en-us/sql-server'
        },
        {
          name: 'Oracle Database',
          logo: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/oracle/oracle-original.svg',
          link: 'https://www.oracle.com/database/'
        },
      ],
      other: [
        {
          name: 'MySQL',
          logo: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/mysql/mysql-original.svg',
          link: 'https://www.mysql.com/'
        },
        {
          name: 'Flutter',
          logo: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/flutter/flutter-original.svg',
          link: 'https://flutter.dev/'
        },
        {
          name: 'GitHub',
          logo: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/github/github-original.svg',
          link: 'https://github.com/'
        },
        {
          name: 'Designing',
          logo: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/photoshop/photoshop-line.svg',
          link: 'https://www.adobe.com/products/photoshop.html'
        },
        {
          name: 'Video Editing',
          logo: 'https://www.svgrepo.com/show/504203/capcut.svg',
          link: 'https://www.capcut.com/'
        }
      ]
    };
  }
};
</script>

<style scoped>
/* Animation Classes */
.animate-fade-in {
  animation: fadeIn 0.8s ease-out forwards;
  opacity: 0;
}

.animate-expand {
  animation: expand 0.8s ease-out forwards;
  transform-origin: center;
  transform: scaleX(0);
}

.animate-card-in {
  animation: cardIn 0.6s cubic-bezier(0.175, 0.885, 0.32, 1.275) forwards;
  opacity: 0;
  transform: translateY(20px);
}

/* Animation Delays */
/* Add this instead */
.delay-0 {
  animation-delay: 0s;
}

.delay-100 {
  animation-delay: 0.1s;
}

.delay-200 {
  animation-delay: 0.2s;
}

.delay-300 {
  animation-delay: 0.3s;
}

.delay-400 {
  animation-delay: 0.4s;
}

.delay-500 {
  animation-delay: 0.5s;
}

.delay-600 {
  animation-delay: 0.6s;
}

.delay-700 {
  animation-delay: 0.7s;
}

.delay-800 {
  animation-delay: 0.8s;
}

.delay-900 {
  animation-delay: 0.9s;
}

.delay-1000 {
  animation-delay: 1s;
}


/* Keyframe Animations */
@keyframes fadeIn {
  from {
    opacity: 0;
  }

  to {
    opacity: 1;
  }
}

@keyframes expand {
  from {
    transform: scaleX(0);
  }

  to {
    transform: scaleX(1);
  }
}

@keyframes cardIn {
  from {
    opacity: 0;
    transform: translateY(20px);
  }

  to {
    opacity: 1;
    transform: translateY(0);
  }
}

/* Dynamic delay classes */
/* @for $i from 0 through 10 {
  .delay-#{$i * 100} {
    animation-delay: #{$i * 0.1s};
  }
} */
</style>
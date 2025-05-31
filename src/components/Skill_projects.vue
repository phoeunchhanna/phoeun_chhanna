<template>
  <section id="education"  class="px-4 py-12 sm:px-6 lg:px-8">
    <div class="text-center">
      <h2 class="text-3xl font-extrabold text-lime-400 sm:text-4xl animate-fade-in-down">Studing University</h2>
      <p class="mx-auto mt-3 max-w-2xl text-xl text-white sm:mt-4 animate-fade-in-down animate-delay-100">
        There is my projects from University
      </p>
    </div>
    <div class="mx-auto max-w-7xl">
      <div class="px-2 py-20">
        <div class="grid grid-cols-1 lg:grid-cols-2 gap-8">
          <!-- Project cards -->
          <div 
            v-for="(project, index) in projects" 
            :key="index" 
            class="bg-white mt-5 lg:flex lg:shadow-lg rounded-lg animate-fade-in-up"
            :style="`--animation-delay: ${index * 100}ms`"
            v-animate-on-scroll
          >
            <div class="lg:w-1/2">
              <div class="lg:scale-110 h-80 bg-cover lg:h-full rounded-b-none border lg:rounded-lg transition-transform duration-500 hover:scale-105"
                :style="{ backgroundImage: `url(${project.image})` }"></div>
            </div>

            <div class="py-12 px-6 lg:px-12 lg:w-1/2 rounded-t-none border lg:rounded-lg">
              <h2 class="text-3xl text-gray-800 font-bold transition-colors duration-300 hover:text-indigo-600">
                {{ project.title }}</h2>
              <ul class="list-disc">
                <li class="text-indigo-600 transition-all duration-300 hover:pl-2">{{ project.subtitle1 }}</li>
                <li class="text-indigo-600 transition-all duration-300 hover:pl-2">{{ project.subtitle2 }}</li>
                <li class="text-indigo-600 transition-all duration-300 hover:pl-2">{{ project.subtitle3 }}</li>
                <li class="text-indigo-600 transition-all duration-300 hover:pl-2">{{ project.subtitle4 }}</li>
                <li class="text-indigo-600 transition-all duration-300 hover:pl-2">{{ project.subtitle5 }}</li>
              </ul>

              <p class="mt-4 text-gray-600 transition-all duration-500">
                <span v-if="!project.showFullDesc">{{ truncateDescription(project.description) }}</span>
                <span v-else>{{ project.description }}</span>
                <button @click="toggleDescription(index)"
                  class="text-indigo-600 hover:text-indigo-800 ml-1 focus:outline-none transition-colors duration-300">
                  {{ project.showFullDesc ? 'Read Less' : 'Read More' }}
                </button>
              </p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import { ChevronLeftIcon, ChevronRightIcon } from '@heroicons/vue/20/solid'
import Foundation from '@/assets/projects/foundation_year.png';
import two_year from '@/assets/projects/two_year.jpg';
import tree_year from '@/assets/projects/tree_yesr.jpg';
import final_year from '@/assets/projects/Final_year.jpg';

export default {
  name: 'ProjectsWithModal',
  components: {
    ChevronLeftIcon,
    ChevronRightIcon
  },
  directives: {
    animateOnScroll: {
      mounted(el) {
        el.style.opacity = '0';
        el.style.transform = 'translateY(20px)';
        el.style.transition = 'opacity 0.6s ease-out, transform 0.6s ease-out';
        
        const observer = new IntersectionObserver((entries) => {
          entries.forEach(entry => {
            if (entry.isIntersecting) {
              el.style.opacity = '1';
              el.style.transform = 'translateY(0)';
              observer.unobserve(el);
            }
          });
        }, { threshold: 0.1 });
        
        observer.observe(el);
      }
    }
  },
  data() {
    return {
      isModalOpen: false,
      selectedProject: null,
      currentPage: 1,
      projects: [
        {
          title: "Foundation Years",
          subtitle1: ".Net Programming",
          subtitle2: "Computer tachnology ",
          subtitle3: "Graphic design",
          subtitle4: "Mathenmatics Computing",
          subtitle5: "Methodology",
          description: "Foundation years have taught me a lot about basic computer skills as well as learning the basics of coding, which has made me knowledgeable and prepared for future studies. Not only that, during my studies, I have implemented the principles that the teachers have given me.",
          image: Foundation,
          buttonText: "See More",
          showFullDesc: false
        },
        {
          title: "Secondary Years",
          subtitle1: "System Admin",
          subtitle2: "DBMS Project",
          subtitle3: "Frontend Web Development",
          subtitle4: "Personal Application",
          subtitle5: "Web Application Development",
          description: "After studying the basic level, I also studied the next level, which made me understand more about Code and Networking. Especially, all the exercises that the professor gave made me study even more to prepare for the next year.",
          image: two_year,
          buttonText: "Shop Now",
          showFullDesc: false
        },
        {
          title: "Third Years",
          subtitle1: "ASP.net & SQL server",
          subtitle2: "Advanced PHP & MYSQL ",
          subtitle3: "Client/Sever  Application Dev ",
          subtitle4: "OOP Java",
          subtitle5: "Network (Admin,Design )",
          description: "Studying in the second year has given me a much better understanding of coding languages ​​and some of the practices, including website and system creation.",
          image: tree_year,
          buttonText: "Participate",
          showFullDesc: false
        },
        {
          title: "Fourth year",
          subtitle1: "Mobile Programming (Base , Advance)",
          subtitle2: "Python Programming ",
          subtitle3: "Blockchain Technology",
          subtitle4: "Internetworking ( Base , Advance)",
          subtitle5: "Project Paper for Information Technolgoy",
          description: "My undergraduate studies from the first year to the fourth year have allowed me to learn many skills and learn new things including Computer, Programming language and networking. During my studies, I worked as a Freelancer and Content Creator about Coding and tip computing in my subjaect.",
          image: final_year,
          buttonText: "Learn More",
          showFullDesc: false
        }
      ]
    }
  },
  methods: {
    toggleDescription(index) {
      this.projects[index].showFullDesc = !this.projects[index].showFullDesc;
    },
    truncateDescription(text) {
      const words = text.split(' ');
      if (words.length <= 10) return text;
      return words.slice(0, 10).join(' ') + '...';
    },
    openModal(project) {
      this.selectedProject = project;
      this.isModalOpen = true;
      document.body.style.overflow = 'hidden';
    },
    closeModal() {
      this.isModalOpen = false;
      document.body.style.overflow = 'auto';
    },
    prevPage() {
      if (this.currentPage > 1) {
        this.currentPage--;
      }
    },
    nextPage() {
      if (this.currentPage < this.totalPages) {
        this.currentPage++;
      }
    },
    goToPage(page) {
      this.currentPage = page;
    }
  },
  computed: {
    paginatedItems() {
      const start = (this.currentPage - 1) * 4; // Assuming 4 items per page
      const end = start + 4;
      return this.projects.slice(start, end);
    },
    totalPages() {
      return Math.ceil(this.projects.length / 4);
    },
    visiblePages() {
      const range = 2;
      const start = Math.max(1, this.currentPage - range);
      const end = Math.min(this.totalPages, this.currentPage + range);

      const pages = [];
      for (let i = start; i <= end; i++) {
        pages.push(i);
      }
      return pages;
    }
  }
}
</script>

<style scoped>
/* Animation classes */
.animate-fade-in-down {
  opacity: 0;
  transform: translateY(-20px);
  animation: fadeInDown 0.6s ease-out forwards;
}

.animate-fade-in-down.animate-delay-100 {
  animation-delay: 0.1s;
}

/* Keyframes */
@keyframes fadeInDown {
  from {
    opacity: 0;
    transform: translateY(-20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

/* Hover effects */
.hover\:scale-105:hover {
  transform: scale(1.05);
}

.transition-transform {
  transition-property: transform;
}

.transition-colors {
  transition-property: color, background-color, border-color, text-decoration-color, fill, stroke;
}

.transition-all {
  transition-property: all;
}

.duration-300 {
  transition-duration: 300ms;
}

.duration-500 {
  transition-duration: 500ms;
}

/* Other styles */
button:disabled {
  opacity: 0.5;
  cursor: not-allowed;
}
</style>
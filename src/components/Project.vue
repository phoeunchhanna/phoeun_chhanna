<template>
    <section id="projects" class="px-4 py-12 sm:px-6 lg:px-8">
        <div class="mx-auto max-w-7xl ">
            <!-- Section Header -->
            <transition appear @before-enter="beforeEnter" @enter="enter">
                <div class="mb-12 text-center">
                    <h2 class="text-3xl font-extrabold text-lime-400 sm:text-4xl">My Projects</h2>
                    <p class="mx-auto mt-3 max-w-2xl text-xl text-white sm:mt-4">
                        Check out some of our recent work and case studies.
                    </p>
                </div>
            </transition>
            <!-- Projects Grid -->
            <div class="grid grid-cols-1 gap-8 sm:grid-cols-2 lg:grid-cols-3  ">
                <transition-group appear @before-enter="beforeStaggerEnter" @enter="staggerEnter" tag="div"
                    class="contents">
                    <div v-for="(project, index) in visibleProjects" :key="index"
                        class="overflow-hidden rounded-lg bg-white  transition-all duration-300 hover:scale-105 hover:shadow-lg hover:shadow-lime-300 shadow-lg shadow-gray-300">
                        <div class="h-48 overflow-hidden cursor-pointer" :class="project.bgColor"
                            @click="openModal(project)">
                            <img :src="project.image" :alt="project.title"
                                class="h-full w-full object-cover transition-transform duration-500 hover:scale-110" />
                        </div>
                        <div class="p-6">
                            <h3 class="text-xl font-semibold text-gray-900">{{ project.title }}</h3>
                            <p class="mt-2 text-gray-600">
                                <span v-if="!project.showFullDescription">
                                    {{ truncateDescription(project.description) }}
                                </span>
                                <span v-else>{{ project.description }}</span>
                                <button @click="toggleDescription(project)"
                                    class="ml-1 text-blue-600 hover:text-blue-800 text-sm">
                                    {{ project.showFullDescription ? 'Show less' : '...Show more' }}
                                </button>
                            </p>
                            <div class="mt-4 flex flex-wrap gap-2">
                                <span v-for="(tag, idx) in project.tags" :key="idx" :class="tag.class"
                                    class="rounded-full px-3 py-1 text-xs font-medium transition-all duration-200 hover:scale-105">
                                    <span v-if="tag.language">Language: {{ tag.language }}</span>
                                    <span v-if="tag.Database">Database: {{ tag.Database }}</span>
                                </span>
                            </div>
                            <div class="mt-4 flex flex-wrap gap-2">
                                <a v-if="project.source" :href="project.source" target="_blank"
                                    rel="noopener noreferrer"
                                    class="inline-flex items-center text-blue-600 hover:text-blue-800 transition-colors duration-200">
                                    GitHub
                                    <svg xmlns="http://www.w3.org/2000/svg" class="ml-1 h-4 w-4" viewBox="0 0 20 20"
                                        fill="currentColor">
                                        <path fill-rule="evenodd"
                                            d="M10.293 5.293a1 1 0 011.414 0l4 4a1 1 0 010 1.414l-4 4a1 1 0 01-1.414-1.414L12.586 11H5a1 1 0 110-2h7.586l-2.293-2.293a1 1 0 010-1.414z"
                                            clip-rule="evenodd" />
                                    </svg>
                                </a>
                                <a v-if="project.video" :href="project.video" target="_blank" rel="noopener noreferrer"
                                    class="inline-flex items-center text-red-600 hover:text-red-800 transition-colors duration-200">
                                    YouTube
                                    <svg xmlns="http://www.w3.org/2000/svg" class="ml-1 h-4 w-4" viewBox="0 0 20 20"
                                        fill="currentColor">
                                        <path fill-rule="evenodd"
                                            d="M10.293 5.293a1 1 0 011.414 0l4 4a1 1 0 010 1.414l-4 4a1 1 0 01-1.414-1.414L12.586 11H5a1 1 0 110-2h7.586l-2.293-2.293a1 1 0 010-1.414z"
                                            clip-rule="evenodd" />
                                    </svg>
                                </a>
                                <a v-if="project.demo" :href="project.demo" target="_blank" rel="noopener noreferrer"
                                    class="inline-flex items-center text-green-600 hover:text-green-800 transition-colors duration-200">
                                    Live Demo
                                    <svg xmlns="http://www.w3.org/2000/svg" class="ml-1 h-4 w-4" viewBox="0 0 20 20"
                                        fill="currentColor">
                                        <path fill-rule="evenodd"
                                            d="M10.293 5.293a1 1 0 011.414 0l4 4a1 1 0 010 1.414l-4 4a1 1 0 01-1.414-1.414L12.586 11H5a1 1 0 110-2h7.586l-2.293-2.293a1 1 0 010-1.414z"
                                            clip-rule="evenodd" />
                                    </svg>
                                </a>
                            </div>
                        </div>
                    </div>
                </transition-group>
            </div>
            <transition appear @before-enter="beforeEnter" @enter="enter">
                <!-- View More Button -->
                <div class="mt-12 text-center">
                    <button @click="showAllProjects = !showAllProjects"
                        class="inline-flex items-center rounded-md border border-transparent bg-blue-600 px-6 py-3 text-base font-medium text-white shadow-sm hover:bg-blue-700 transition-colors duration-300 hover:shadow-md">
                        {{ showAllProjects ? 'Show less' : 'View all projects' }}
                    </button>
                </div>
            </transition>
        </div>

        <!-- Project Detail Modal -->
        <transition name="fade">
            <div v-if="selectedProject" class="fixed inset-0 z-50 flex items-center justify-center p-4">
                <div class="fixed inset-0 bg-black bg-opacity-75 transition-opacity duration-300"
                    @click="selectedProject = null"></div>

                <transition name="modal">
                    <div
                        class="relative w-full max-w-6xl max-h-[95vh] overflow-y-auto rounded-2xl bg-white shadow-2xl transform transition-all duration-300">
                        <button @click="selectedProject = null"
                            class="absolute top-6 right-6 z-10 p-3 rounded-full bg-gray-100 hover:bg-gray-200 transition-colors duration-200 shadow-lg">
                            <svg xmlns="http://www.w3.org/2000/svg" class="h-8 w-8 text-gray-700" fill="none"
                                viewBox="0 0 24 24" stroke="currentColor">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                                    d="M6 18L18 6M6 6l12 12" />
                            </svg>
                        </button>

                        <div class="grid lg:grid-cols-2 gap-0">
                            <!-- Project Image (Full View) -->
                            <div class="relative h-full min-h-[300px] bg-gray-100">
                                <img :src="selectedProject.image" :alt="selectedProject.title"
                                    class="absolute inset-0 w-full h-full object-contain p-8 cursor-zoom-in"
                                    @click="toggleImageZoom" />

                                <!-- Zoomed Image Overlay -->
                                <transition name="zoom">
                                    <div v-if="isImageZoomed"
                                        class="fixed inset-0 z-50 bg-black bg-opacity-90 flex items-center justify-center p-4"
                                        @click.self="isImageZoomed = false">
                                        <div class="relative max-w-full max-h-full">
                                            <img :src="selectedProject.image" :alt="selectedProject.title"
                                                class="max-w-[90vw] max-h-[90vh] object-contain" />
                                            <button @click="isImageZoomed = false"
                                                class="absolute -top-12 right-0 p-2 text-white hover:text-gray-300">
                                                <svg xmlns="http://www.w3.org/2000/svg" class="h-8 w-8" fill="none"
                                                    viewBox="0 0 24 24" stroke="currentColor">
                                                    <path stroke-linecap="round" stroke-linejoin="round"
                                                        stroke-width="2" d="M6 18L18 6M6 6l12 12" />
                                                </svg>
                                            </button>
                                        </div>
                                    </div>
                                </transition>
                            </div>

                            <!-- Project Details (Larger Form) -->
                            <div class="p-10 overflow-y-auto max-h-[95vh]">
                                <h3 class="text-4xl font-bold text-gray-900 mb-6">{{ selectedProject.title }}</h3>
                                <p class="text-xl text-gray-600 mb-8 leading-relaxed">{{ selectedProject.description }}
                                </p>
                                <h4 >Facture :</h4>
                                <ul class="list-disc ml-5 mb-3">
                                    <li class="text-indigo-600 transition-all duration-300 hover:pl-2">{{ selectedProject.fecture1 }}</li>
                                    <li class="text-indigo-600 transition-all duration-300 hover:pl-2">{{ selectedProject.fecture2 }}</li>
                                    <li class="text-indigo-600 transition-all duration-300 hover:pl-2">{{ selectedProject.fecture3 }}</li>
                                    <li class="text-indigo-600 transition-all duration-300 hover:pl-2">{{ selectedProject.fecture4 }}</li>
                                    <li class="text-indigo-600 transition-all duration-300 hover:pl-2">{{ selectedProject.fecture5 }}</li>
                                    <li class="text-indigo-600 transition-all duration-300 hover:pl-2">{{ selectedProject.fecture6 }}</li>
                                    <li class="text-indigo-600 transition-all duration-300 hover:pl-2">{{ selectedProject.fecture7 }}</li>
                                    <li class="text-indigo-600 transition-all duration-300 hover:pl-2">{{ selectedProject.fecture8 }}</li>
                                    <li class="text-indigo-600 transition-all duration-300 hover:pl-2">{{ selectedProject.fecture9 }}</li>
                                    <li class="text-indigo-600 transition-all duration-300 hover:pl-2">{{ selectedProject.fecture10 }}</li>
                                </ul>



                                <div class="mb-8">
                                    <h4 class="text-2xl font-semibold text-gray-800 mb-4">Technologies Used</h4>
                                    <div class="flex flex-wrap gap-3">
                                        <span v-for="(tag, idx) in selectedProject.tags" :key="idx" :class="tag.class"
                                            class="rounded-full px-4 py-2 text-sm font-medium">
                                            <span v-if="tag.language">{{ tag.language }}</span>
                                            <span v-if="tag.Database">{{ tag.Database }}</span>
                                        </span>
                                    </div>
                                </div>

                                <div class="space-y-5">
                                    <a v-if="selectedProject.source" :href="selectedProject.source" target="_blank"
                                        rel="noopener noreferrer"
                                        class="flex items-center px-6 py-4 text-black rounded-xl hover:bg-gray-200 transition-all duration-200 text-lg">
                                        <svg class="w-7 h-7 mr-3 text-gray-700" fill="currentColor" viewBox="0 0 24 24">
                                            <path fill-rule="evenodd"
                                                d="M12 2C6.477 2 2 6.484 2 12.017c0 4.425 2.865 8.18 6.839 9.504.5.092.682-.217.682-.483 0-.237-.008-.868-.013-1.703-2.782.605-3.369-1.343-3.369-1.343-.454-1.158-1.11-1.466-1.11-1.466-.908-.62.069-.608.069-.608 1.003.07 1.531 1.032 1.531 1.032.892 1.53 2.341 1.088 2.91.832.092-.647.35-1.088.636-1.338-2.22-.253-4.555-1.113-4.555-4.951 0-1.093.39-1.988 1.029-2.688-.103-.253-.446-1.272.098-2.65 0 0 .84-.27 2.75 1.026A9.564 9.564 0 0112 6.844c.85.004 1.705.115 2.504.337 1.909-1.296 2.747-1.027 2.747-1.027.546 1.379.202 2.398.1 2.651.64.7 1.028 1.595 1.028 2.688 0 3.848-2.339 4.695-4.566 4.943.359.309.678.92.678 1.855 0 1.338-.012 2.419-.012 2.747 0 .268.18.58.688.482A10.019 10.019 0 0022 12.017C22 6.484 17.522 2 12 2z"
                                                clip-rule="evenodd" />
                                        </svg>
                                        View Source Code on GitHub
                                    </a>

                                    <a v-if="selectedProject.video" :href="selectedProject.video" target="_blank"
                                        rel="noopener noreferrer"
                                        class="flex items-center px-6 py-4 text-black rounded-xl hover:bg-gray-200 transition-all duration-200 text-lg">
                                        <svg class="w-7 h-7 mr-3 text-red-600" fill="currentColor" viewBox="0 0 24 24">
                                            <path
                                                d="M19.615 3.184c-3.604-.246-11.631-.245-15.23 0-3.897.266-4.356 2.62-4.385 8.816.029 6.185.484 8.549 4.385 8.816 3.6.245 11.626.246 15.23 0 3.897-.266 4.356-2.62 4.385-8.816-.029-6.185-.484-8.549-4.385-8.816zm-10.615 12.816v-8l8 3.993-8 4.007z" />
                                        </svg>
                                        Watch Project Demo on YouTube
                                    </a>

                                    <a v-if="selectedProject.demo" :href="selectedProject.demo" target="_blank"
                                        rel="noopener noreferrer"
                                        class="flex items-center px-6 py-4 bg-blue-600 text-white rounded-xl hover:bg-blue-700 transition-all duration-200 text-lg">
                                        <svg class="w-7 h-7 mr-3" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                                                d="M21 12a9 9 0 01-9 9m9-9a9 9 0 00-9-9m9 9H3m9 9a9 9 0 01-9-9m9 9c1.657 0 3-4.03 3-9s-1.343-9-3-9m0 18c-1.657 0-3-4.03-3-9s1.343-9 3-9m-9 9a9 9 0 019-9" />
                                        </svg>
                                        View Live Demo
                                    </a>
                                </div>

                            </div>
                        </div>
                    </div>
                </transition>
            </div>
        </transition>

        <!-- Add Project Modal (existing code remains the same) -->
    </section>
</template>

<script>
import birthCertificateImg from '@/assets/projects/brithcertificate.png';
import loan from '@/assets/projects/loan.jpg';
import computer from '@/assets/projects/Computer_store.png';
import phone_store from '@/assets/projects/Phone _Store_mgt.png';
import phone_order from '@/assets/projects/Phon_Order.png';
import Restaurants from '@/assets/projects/restaurants_web.jpg';
import savuth_port from '@/assets/projects/savuth_port.png';
import { gsap } from 'gsap';
export default {
    name: 'ProjectsSection',
    data() {
        return {
            selectedProject: null,
            showAllProjects: false,
            isImageZoomed: false,
            newProject: {
                title: '',
                description: '',
                fecture1: '',
                fecture2: '',
                fecture3: '',
                fecture4: '',
                fecture5: '',
                fecture6: '',
                fecture7: '',
                fecture8: '',
                fecture9: '',
                fecture10: '',
                image: '',
                bgColor: 'bg-blue-500',
                source: '',
                video: '',
                demo: '',
                tags: [
                    { language: '', class: 'bg-blue-100 text-blue-800' },
                    { Database: '', class: 'bg-green-100 text-green-800' },
                ],
                showFullDescription: false
            },
            projects: [
                {
                    title: 'Birth Certificate App',
                    description: 'The birth certificate system is a program used to manage birth certificates, birth certificates, and not only that, we can download birth certificates, birth certificates in PDF format, and can know the total report of birth certificates.',
                    fecture1: 'Home Page Manage ',
                    fecture2: 'Birth Manage',
                    fecture3: 'Birth Certificate Manage',
                    fecture4: 'Mother Manage',
                    fecture5: 'Father Mange',
                    fecture6: 'Mother address Maneg',
                    fecture7: 'Father address Manage',
                    fecture8: 'Baby address Manage',
                    fecture9: 'Report Birth ',
                    fecture10: 'Report Birth Certicate Manage',
                    image: birthCertificateImg,
                    bgColor: 'bg-blue-500',
                    source: 'https://github.com/phoeunchhanna',
                    video: 'https://www.youtube.com/@ChhannaCode2002',
                    demo: 'https://birthcertificate.me/public/',
                    tags: [
                        { language: 'Laravel Framework', class: 'bg-blue-100 text-blue-800' },
                        { Database: 'MySQL', class: 'bg-green-100 text-green-800' },
                    ],
                    showFullDescription: false
                },
                {
                    title: 'Website Loan',
                    description: 'Website Loan is a website created to allow users to apply for loans to do business or invest in something. Also, I can not show the website because it is a client requirement.',
                    fecture1: 'login session',
                    fecture2: 'Customer  Manage',
                    fecture3: 'laoning  Manage',
                    fecture4: 'Payment  Manage',
                    fecture5: 'KHcphoto  Mange',
                    fecture6: 'Profile Invoice Maneg',
                    fecture7: 'Wallet Manage',
                    fecture8: 'Installment  Manage',
                    fecture9: 'view profile Manage',
                    fecture10: 'Reporting data ',
                    image: loan,
                    bgColor: 'bg-blue-500',
                    source: 'https://github.com/phoeunchhanna',
                    video: 'https://www.youtube.com/@ChhannaCode2002',
                    // demo: 'https://birthcertificate.me/public/',
                    tags: [
                        { language: 'Vue js', class: 'bg-blue-100 text-blue-800' },
                        { Database: 'Firebase /Firestore', class: 'bg-green-100 text-green-800' },
                    ],
                    showFullDescription: false
                },
                {
                    title: 'Computer Store',
                    description: 'Computer Store is a website that allows customers who do not want to go to the store to buy, to also order through this website. The process and invoice are the same as purchasing in the store.',
                    fecture1: 'login session',
                    fecture2: 'brand  Manage',
                    fecture3: 'Category Manage',
                    fecture4: 'Products Manage',
                    fecture5: 'Saleing  Mange',
                    fecture6: 'Saling Invoice Maneg',
                    fecture7: 'Saling Report Manage',
                    fecture8: 'Stock In  Manage',
                    fecture9: 'Outstock Manage',
                    fecture10: 'Reporting ',
                    image: computer,
                    bgColor: 'bg-blue-500',
                    source: 'https://github.com/phoeunchhanna',
                    video: 'https://youtu.be/KB6B598HI_M',
                    // demo: 'https://birthcertificate.me/public/',
                    tags: [
                        { language: 'ASP.net', class: 'bg-blue-100 text-blue-800' },
                        { Database: 'MySql', class: 'bg-green-100 text-green-800' },
                    ],
                    showFullDescription: false
                },
                {
                    title: 'Phone Store System',
                    description: 'Phone Store App is a web-based application used to facilitate sales and provide clarity on sales and customer information, as well as daily, monthly, and annual reports, and much more.',
                    fecture1: 'Sale Manage',
                    fecture2: 'Sale Return Manage',
                    fecture3: 'Product Manage',
                    fecture4: 'Purchase Manage',
                    fecture5: 'Purchase Payment Manage',
                    fecture6: 'Report Saleing',
                    fecture7: 'Report Sale Return',
                    fecture8: 'Report Product',
                    fecture9: 'Report Purchase',
                    fecture10: 'Report Purchase Payment  ',
                    image: phone_store,
                    bgColor: 'bg-blue-500',
                    source: 'https://github.com/sandey2/my_project',
                    video: 'https://youtu.be/o4qvuYZeA5I',
                    // demo: 'https://birthcertificate.me/public/',
                    tags: [
                        { language: 'Laravel', class: 'bg-blue-100 text-blue-800' },
                        { Database: 'MySql', class: 'bg-green-100 text-green-800' },
                    ],
                    showFullDescription: false
                },
                {
                    title: ' Phone Store Order',
                    description: 'Phone Order is a website that allows customers who do not want to go to the store to buy, to also order through this website. The process and invoice are the same as purchasing in the store.',
                    fecture1: 'Sale Manage',
                    fecture2: 'history Manage',
                    fecture3: 'Products Manage',
                    fecture4: 'pofile Manage',
                    fecture5: 'update profile Manage',
                    fecture6: 'Saleing Invoice',
                    fecture7: 'expice data ',
                    fecture8: 'Delevery ',
                    fecture9: 'Exchange',
                    fecture10: 'view all products ',
                    image: phone_order,
                    bgColor: 'bg-blue-500',
                    source: 'https://github.com/sandey2/my_project',
                    video: 'https://youtube.com/watch?v=example1',
                    // demo: 'https://birthcertificate.me/public/',
                    tags: [
                        { language: 'Laravel', class: 'bg-blue-100 text-blue-800' },
                        { Database: 'MySql', class: 'bg-green-100 text-green-800' },
                    ],
                    showFullDescription: false
                },
                {
                    title: 'Restaurants Website',
                    description: 'A restaurant website is a digital platform that serves as an online presence for dining establishments, providing information and services to potential and existing customers.',
                    fecture1: 'Online Menu',
                    fecture2: 'Online Table Reservation',
                    fecture3: 'Online Ordering & Delivery',
                    fecture4: 'Responsive Design',
                    fecture5: 'Gallery or Virtual Tour',
                    fecture6: 'Contact Information & Map',
                    fecture7: 'Opening Hours',
                    fecture8: 'Customer Reviews or Testimonials ',
                    fecture9: 'Special Offers or Events Section',
                    fecture10: 'Social Media Integration',
                    image: Restaurants,
                    bgColor: 'bg-blue-500',
                    // source: 'https://github.com/example/birth-certificate-app',
                    // video: 'https://youtube.com/watch?v=example1',
                    // demo: 'https://birthcertificate.me/public/',
                    tags: [
                        { language: 'Vue js', class: 'bg-blue-100 text-blue-800' },
                        { Database: 'Firebase', class: 'bg-green-100 text-green-800' },
                    ],
                    showFullDescription: false
                },
                {
                    title: 'Savuth Designer Portofolio ',
                    description: 'A portfolio website is a digital platform that show hime project about desginger to for all people , Especially for comapany and cominunity than something els .',
                     fecture1: ' Menu',
                    fecture2:'About profile',
                    fecture3: 'Get CV ',
                    fecture4: 'Skill',
                    fecture5: 'Value of Skill',
                    fecture6: 'Project design',
                    fecture7: 'See full infor project',
                    fecture8: 'contect ',
                    fecture9: 'scane contect',
                    fecture10: 'Design service',
                    image: savuth_port,
                    bgColor: 'bg-blue-500',
                    source: 'https://github.com/phoeunchhanna/Savuth_portfolio',
                    // video: 'https://youtube.com/watch?v=example1',
                    demo: 'https://savuth-portfolio.onrender.com/',
                    tags: [
                        { language: 'Vue js', class: 'bg-blue-100 text-blue-800' },
                        { Database: 'Tailwind CSS', class: 'bg-green-100 text-green-800' },
                    ],
                    showFullDescription: false
                },

            ],
        };
    },
    computed: {
        visibleProjects() {
            return this.showAllProjects ? this.projects : this.projects.slice(0, 6);
        }
    },
    methods: {
        toggleImageZoom() {
            this.isImageZoomed = !this.isImageZoomed;
        },
        openModal(project) {
            this.selectedProject = project;
        },
        truncateDescription(description) {
            const words = description.split(' ');
            return words.length > 10
                ? words.slice(0, 10).join(' ')
                : description;
        },
        toggleDescription(project) {
            project.showFullDescription = !project.showFullDescription;
        },
        submitProject() {
            this.projects.push({ ...this.newProject });
            this.selectedProject = null;
            this.resetNewProject();
        },
        resetNewProject() {
            this.newProject = {
                title: '',
                description: '',
                image: '',
                bgColor: 'bg-blue-500',
                source: '',
                video: '',
                demo: '',
                tags: [
                    { language: '', class: 'bg-blue-100 text-blue-800' },
                    { Database: '', class: 'bg-green-100 text-green-800' },
                ],
                showFullDescription: false
            };
        },
        // Animation methods
        beforeEnter(el) {
            el.style.opacity = 0;
            el.style.transform = 'translateY(20px)';
        },
        enter(el, done) {
            gsap.to(el, {
                opacity: 1,
                y: 0,
                duration: 0.8,
                ease: 'power2.out',
                onComplete: done
            });
        },
        beforeStaggerEnter(el) {
            el.style.opacity = 0;
            el.style.transform = 'translateY(30px)';
        },
        staggerEnter(el, done) {
            const delay = el.dataset.index * 0.15;

            gsap.to(el, {
                opacity: 1,
                y: 0,
                duration: 0.6,
                delay: delay,
                ease: 'back.out(1.7)',
                onComplete: done
            });
        },
    },
    mounted() {
        // Add scroll animations
        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.classList.add('animate-fadeInUp');
                    observer.unobserve(entry.target);
                }
            });
        }, { threshold: 0.1 });

        document.querySelectorAll('.project-card').forEach(card => {
            observer.observe(card);
        });
    }
};
</script>

<style scoped>
/* Fade transition for modal backdrop */
.fade-enter-active,
.fade-leave-active {
    transition: opacity 0.3s ease;
}

.fade-enter-from,
.fade-leave-to {
    opacity: 0;
}

/* Modal transition */
.modal-enter-active,
.modal-leave-active {
    transition: all 0.3s ease;
}

.modal-enter-from,
.modal-leave-to {
    opacity: 0;
    transform: translateY(20px);
}

/* Hover animations */
.hover-zoom {
    transition: transform 0.3s ease;
}

.hover-zoom:hover {
    transform: scale(1.05);
}

/* Smooth transitions for buttons */
.button-transition {
    transition: all 0.2s ease-in-out;
}

/* Card hover effect */
.card-hover {
    transition: all 0.3s ease;
}

.card-hover:hover {
    transform: translateY(-5px);
    box-shadow: 0 10px 20px rgba(0, 0, 0, 0.1);
}

/* animation */
.animate-fadeInUp {
    animation: fadeInUp 0.6s ease-out forwards;
}

@keyframes fadeInUp {
    from {
        opacity: 0;
        transform: translateY(20px);
    }

    to {
        opacity: 1;
        transform: translateY(0);
    }
}

/* Page load animations */
.project-card {
    opacity: 0;
    transform: translateY(20px);
    animation: fadeInUp 0.6s ease-out forwards;
    animation-delay: calc(var(--animation-order) * 0.1s);
}

/* Enhanced hover animations */
.hover-zoom {
    transition: transform 0.3s cubic-bezier(0.25, 0.1, 0.25, 1);
}

.hover-zoom:hover {
    transform: scale(1.05) translateY(-5px);
}

/* Smooth transitions for buttons */
.button-transition {
    transition: all 0.3s cubic-bezier(0.25, 0.1, 0.25, 1);
}

/* Card hover effect with shadow animation */
.card-hover {
    transition: all 0.4s cubic-bezier(0.25, 0.1, 0.25, 1);
}

.card-hover:hover {
    transform: translateY(-8px);
    box-shadow: 0 15px 30px rgba(0, 0, 0, 0.15);
}

/* Add this for a subtle scale animation on page load */
@keyframes subtleScale {
    from {
        transform: scale(0.98);
        opacity: 0;
    }

    to {
        transform: scale(1);
        opacity: 1;
    }
}

section {
    animation: subtleScale 0.6s ease-out;
}
</style>
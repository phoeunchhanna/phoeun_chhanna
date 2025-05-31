<template>
    <footer id="social"  class="bg-slate-800 text-white py-12 px-4 sm:px-6 lg:px-8  bg-grid-pattern">
        <div class="max-w-7xl mx-auto ">
            <!-- Header section -->
            <div class="text-center mb-8">
                <h2 class="text-3xl font-bold mb-2">Web Developer and Databes Specialist </h2>
                <p class="text-gray-400 max-w-2xl mx-auto"></p>
                    This Website it really my Profile , Experience , and Education .
                    <p>I have service for building Website and System .</p> 
                    <p>I'm finding same job to improve my skill.</p>
                    
                
            </div>

            <!-- Social Media Icons -->
            <div class="flex justify-center space-x-6 mb-8">
                <a v-for="link in socialLinks" :key="link.name" :href="link.href" target="_blank"
                    rel="noopener noreferrer" class="text-gray-500 hover:text-white transition-colors duration-300">
                    <img :src="link.icon" :alt="link.name" class="w-8 h-8 object-contain" />
                    <span class="sr-only">{{ link.name }}</span>
                </a>
            </div>

            <!-- Divider -->
            <div class="border-t border-lime-300 my-10"></div>

            <!-- Bottom section -->
            <div class="flex flex-col md:flex-row justify-between items-center">
                <!-- Copyright -->
                <div class="text-gray-400 mb-4 md:mb-0">
                    Copyright ©2025 Web Developer
                </div>

                <!-- Navigation links -->
                <nav class="flex flex-wrap justify-center gap-4 sm:gap-6">
                    <a href="https://web.facebook.com/profile.php?id=100092645402500"><h6 class="text-gray-400">Chhanna Code</h6></a>
                </nav>
            </div>
        </div>
    </footer>
</template>

<script>
export default {
    name: 'FooterComponent',
    data() {
        return {
            socialLinks: [
                {
                    name: 'Facebook',
                    href: 'https://web.facebook.com/profile.php?id=100092645402500',
                    icon: 'https://cdn.jsdelivr.net/gh/simple-icons/simple-icons@develop/icons/facebook.svg',
                },
                {
                    name: 'YouTube',
                    href: 'https://www.youtube.com/@ChhannaCode2002',
                    icon: 'https://cdn.jsdelivr.net/gh/simple-icons/simple-icons@develop/icons/youtube.svg',
                },
                {
                    name: 'LinkedIn',
                    href: 'https://www.linkedin.com/in/chhanna-phoeun-6a4668257/',
                    icon: 'https://img.icons8.com/fluent/30/000000/linkedin-2.png',
                },
                {
                    name: 'Telegram',
                    href: 'https://t.me/Chhanna_phoeun',
                    icon: 'https://cdn.jsdelivr.net/gh/simple-icons/simple-icons@develop/icons/telegram.svg',
                },
            ],
        };
    }
}
</script>

<style scoped>
/* Ensure icons are visible on dark backgrounds */
.bg-grid-pattern {
  background-image: 
    linear-gradient(to right, rgba(255,255,255,0.03) 1px, transparent 1px),
    linear-gradient(to bottom, rgba(255,255,255,0.03) 1px, transparent 1px);
  background-size: 40px 40px;
}

img {
  filter: brightness(0) invert(0.8);
  transition: filter 0.3s ease;
}

a:hover img {
  filter: brightness(0) invert(1);
}
</style>
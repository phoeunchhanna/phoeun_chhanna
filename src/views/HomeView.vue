<template>
  <div class="background-container " >
    <Home/>
    <Header/>
    <Profile/>
    <skill/>
    <Project/>
    <Skill_projects/>
    <Footer/>
  </div>
</template>

<script>
import Header from '@/components/Header.vue';
import Home from '@/components/Home.vue';
import skill from '@/components/skill.vue';
import Project from '@/components/Project.vue';
import Footer from '@/components/Footer.vue';
import Skill_projects from '@/components/Skill_projects.vue';
import Profile from '@/components/Profile.vue';

export default {
  name: 'HomeView',
  components: {
    Header,
    Home,
    skill,
    Project,
    Footer,
    Skill_projects,
    Profile
  }
  // Removed the myImage data property since we're using gradient
}
</script>

<style scoped>
  .background-container {
  position: relative;
  min-height: 100vh;
  color: rgb(58, 57, 57);
  font-family: sans-serif;
  padding: 2rem;
}

.background-container::before {
  content: "";
  background-image: url('@/assets/image/coding.jpg');
  background-position: center;
  background-repeat: no-repeat;
  background-attachment: fixed;
  background-size: cover;
  opacity: 0.8;
  position: absolute;
  top: 0;
  left: 0;
  bottom: 0;
  right: 0;
  z-index: -1;
}
</style>
<template>
  <v-app :theme="theme">
    <HeaderSection :theme="theme" @toggle-theme="toggleTheme" />

    <v-main :class="theme === 'light' ? 'galaxy-bg-light' : 'galaxy-bg-dark'">
      <v-container fluid>
        <HomeSection :theme="theme" />
        <AboutSection :theme="theme" />
        <EducationSection :theme="theme" :education="education" />
        <SkillsSection :theme="theme" :skills="skills" />
        <ServicesSection :theme="theme" :services="services" />
        <ProjectsSection :theme="theme" :projects="projects" />
        <ContactSection :theme="theme" @submit-form="submitForm" />
      </v-container>
    </v-main>

    <AppFooter :theme="theme" />

    <ScrollToTopButton :theme="theme" @scroll-to-top="scrollToTop" />
  </v-app>
</template>

<script>
import HeaderSection from './components/HeaderSection.vue'
import HomeSection from './components/HomeSection.vue'
import AboutSection from './components/AboutSection.vue'
import EducationSection from './components/EducationSection.vue'
import SkillsSection from './components/SkillsSection.vue'
import ServicesSection from './components/ServicesSection.vue'
import ProjectsSection from './components/ProjectsSection.vue'
import ContactSection from './components/ContactSection.vue'
import AppFooter from './components/AppFooter.vue'
import ScrollToTopButton from './components/ScrollToTopButton.vue'

export default {
  name: 'App',
  components: {
    HeaderSection,
    HomeSection,
    AboutSection,
    EducationSection,
    SkillsSection,
    ServicesSection,
    ProjectsSection,
    ContactSection,
    AppFooter,
    ScrollToTopButton
  },
  data: () => ({
    theme: 'dark',
    education: [
        { school: 'University of XYZ', degree: 'Bachelor of Science in IT', year: '2019 - 2023', achievements: ['Dean\'s List', 'Cum Laude']},
        { school: 'High School ABC', degree: 'High School Diploma', year: '2015 - 2019', achievements: ['Valedictorian', 'Math Club President']},
        // Add more items as needed
      ],
    skills: [
      { name: 'HTML', icon: 'mdi-language-html5', description: 'Structuring web content', percentage: 100 },
      { name: 'CSS', icon: 'mdi-language-css3', description: 'Styling and layout', percentage: 100 },
      { name: 'JavaScript', icon: 'mdi-language-javascript', description: 'Interactive web development', percentage: 60 },
      { name: 'Vue.js', icon: 'mdi-vuejs', description: 'Frontend framework', percentage: 75 },
      { name: 'PostgreSQL', icon: 'mdi-database', description: 'Backend database', percentage: 90 },
      { name: 'UI/UX Design', icon: 'mdi-palette', description: 'Creating user-friendly interfaces', percentage: 80 },
    ],
    services: [
      { name: 'Web Development', icon: 'mdi-web', description: 'Creating responsive and dynamic websites' },
      { name: 'UI/UX Design', icon: 'mdi-palette', description: 'Designing intuitive and attractive user interfaces' },
      { name: 'Database Management', icon: 'mdi-database', description: 'Efficient data storage and retrieval solutions' },
    ],
    projects: [
      { name: 'Attendance Checker', image: require('@/assets/attendances.png'), description: 'An automated system for tracking and managing attendance', link: '#' },
      { name: 'Text-based Game', image: require('@/assets/text-based.png'), description: 'An interactive narrative adventure game played through text commands', link: 'https://github.com/Caeilanlightwood77/text-based-game' },
      { name: 'Simple Calculator', image: require('@/assets/calculator.png'), description: 'A user-friendly calculator application with basic arithmetic operations', link: 'https://github.com/Caeilanlightwood77/simple_calculator' },
      { name: 'BootStrap Portfolio Websites', image: require('@/assets/Tailwindcss.png'), description: 'Custom-designed portfolio websites to showcase professional work', link: 'https://seclet4ever143.github.io/Bootstrap-Personal-Portfolio/' },
      { name: 'TailWindCss Portfolio Websites', image: require('@/assets/BootStrap.png'), description: 'Custom-designed portfolio websites to showcase professional work', link: 'https://seclet4ever143.github.io/Tailwindcss-Personal/' },
      { name: 'Weather App', image: require('@/assets/Weather-App.png'), description: 'A real-time weather application providing accurate forecasts', link: 'https://weather-app-inky-nu-90.vercel.app/' },
      { name: 'To-Do List', image: require('@/assets/ToDoList.png'), description: 'A task management application to help organize daily activities', link: 'https://puspus-to-do-list.vercel.app/' },
    ],
  }),
  methods: {
    toggleTheme() {
      this.theme = this.theme === 'light' ? 'dark' : 'light'
    },
    submitForm(form) {
      console.log('Form submitted:', form)
      console.log(`Sending email to seclet4ever@gmail.com`)
      console.log(`From: ${form.name} (${form.email})`)
      console.log(`Subject: ${form.subject}`)
      console.log(`Message: ${form.message}`)
      
      alert('Thank you for your message! I will get back to you soon.')
    },
    scrollToTop() {
      window.scrollTo({
        top: 0,
        behavior: 'smooth'
      })
    },
  },
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@300;400;500;700&display=swap');

html {
  scroll-behavior: smooth;
}

.v-application {
  font-family: 'Roboto', sans-serif;
}

.galaxy-bg-light {
  background-image: 
    radial-gradient(#e6d7c3 1px, transparent 1px),
    radial-gradient(#e6d7c3 1px, transparent 1px);
  background-size: 50px 50px;
  background-position: 0 0, 25px 25px;
  background-color: #f5f0e8;
}

.galaxy-bg-dark {
  background-image: 
    radial-gradient(#4a4a4a 1px, transparent 1px),
    radial-gradient(#4a4a4a 1px, transparent 1px);
  background-size: 50px 50px;
  background-position: 0 0, 25px 25px;
  background-color: #2a2a2a;
}

.v-application.v-theme--light {
  --v-theme-primary: #8c7851;
  --v-theme-beige: #d7cdb8;
  --v-theme-beige-lighten-4: #f5f0e8;
  --v-theme-beige-darken-4: #8c7851;
}

.v-application.v-theme--dark {
  --v-theme-primary: #d7cdb8;
  --v-theme-beige: #8c7851;
  --v-theme-beige-lighten-4: #4a4a4a;
  --v-theme-beige-darken-4: #2a2a2a;
}

.black--text {
  color: black !important;
}

@media (max-width: 600px) {
  .v-container {
    padding: 16px !important;
  }

  .v-col {
    padding: 8px !important;
  }

  .text-h3 {
    font-size: 1.75rem !important;
  }

  .text-h4 {
    font-size: 1.5rem !important;
  }

  .text-h5 {
    font-size: 1.25rem !important;
  }

  .text-h6 {
    font-size: 1rem !important;
  }
}
</style>
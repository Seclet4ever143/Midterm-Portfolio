<template>
  <v-app :theme="theme">
    <v-app-bar app :color="theme === 'light' ? 'grey-lighten-2' : 'grey-darken-4'">
      <v-app-bar-nav-icon @click.stop="drawer = !drawer"></v-app-bar-nav-icon>
      <v-toolbar-title>Aedrian Puspus | Web Developer</v-toolbar-title>
      <v-spacer></v-spacer>
      <v-btn icon @click="toggleTheme">
        <v-icon>{{ theme === 'light' ? 'mdi-weather-night' : 'mdi-weather-sunny' }}</v-icon>
      </v-btn>
      <v-btn icon href="https://github.com/Seclet4ever143" target="_blank">
        <v-icon>mdi-github</v-icon>
      </v-btn>
      <v-btn icon href="/" target="_blank">
        <v-icon>mdi-linkedin</v-icon>
      </v-btn>
    </v-app-bar>

    <v-navigation-drawer v-model="drawer" app :color="theme === 'light' ? 'grey-lighten-2' : 'grey-darken-4'">
      <v-container class="d-flex flex-column fill-height">
        <v-row justify="center" class="mt-4">
          <v-col cols="12" class="text-center">
            <v-avatar size="100">
              <v-img src="@/assets/logo.png" alt="Logo"></v-img>
            </v-avatar>
          </v-col>
        </v-row>
        <v-row class="flex-grow-1 align-center">
          <v-col cols="12">
            <v-list class="text-center">
              <v-list-item v-for="(item, i) in menuItems" :key="i" :href="item.href" @click="drawer = false">
                <template v-slot:prepend>
                  <v-icon :color="theme === 'light' ? 'primary' : 'beige'" class="mx-auto">{{ item.icon }}</v-icon>
                </template>
                <v-list-item-title class="text-center">{{ item.title }}</v-list-item-title>
              </v-list-item>
            </v-list>
          </v-col>
        </v-row>
        <v-row justify="center" class="mb-4">
          <v-col cols="12" class="text-center">
            <v-btn icon @click="toggleTheme">
              <v-icon>{{ theme === 'light' ? 'mdi-weather-night' : 'mdi-weather-sunny' }}</v-icon>
            </v-btn>
          </v-col>
        </v-row>
      </v-container>
    </v-navigation-drawer>

    <v-main :class="theme === 'light' ? 'galaxy-bg-light' : 'galaxy-bg-dark'">
      <v-container fluid>
        <section id="home" class="my-16">
          <v-row align="center" justify="center">
            <v-col cols="12" md="6" class="text-center">
              <v-avatar size="200">
                <v-img src="@/assets/avatar.jpg" alt="Aedrian Puspus"></v-img>
              </v-avatar>
              <h1 class="text-h2 mt-4">Aedrian Puspus</h1>
              <v-slide-y-transition>
                <p class="text-h5 font-weight-light" v-show="showDesignation">Web Developer & Designer</p>
              </v-slide-y-transition>
              <v-btn :color="theme === 'light' ? 'primary' : 'beige'" large class="mt-4 mr-2" href="#contact">Get in Touch</v-btn>
              <v-btn :color="theme === 'light' ? 'primary' : 'beige'" large class="mt-4" href="./assets/YANYAN-RESUME-Final.pdf" download>Download Resume</v-btn>
            </v-col>
          </v-row>
        </section>

        <section id="about" class="my-16">
          <v-row justify="center">
            <v-col cols="12" md="10">
              <v-card :color="theme === 'light' ? 'beige-lighten-4' : 'beige-darken-4'">
                <v-card-title class="text-h3 justify-center">About Me</v-card-title>
                <v-card-text>
                  <v-row align="center">
                    <v-col cols="12" md="4" class="text-center">
                      <v-avatar size="250" class="elevation-5">
                        <v-img src="@/assets/avatar.jpg" alt="Aedrian Puspus"></v-img>
                      </v-avatar>
                    </v-col>
                    <v-col cols="12" md="8">
                      <p class="text-body-1">Hello! I'm Aedrian Puspus, a 3rd year BSIT student from Caraga State University. I'm passionate about web development and eager to learn new technologies. My journey in the world of coding has been exciting, and I'm always looking for new challenges to expand my skills.</p>
                      <p class="text-body-1">As an aspiring web developer, I'm committed to creating user-friendly and visually appealing websites. I believe in the power of continuous learning and am excited about the endless possibilities in the field of web development.</p>
                      <h3 class="text-h5 mt-4">Education</h3>
                      <ul class="text-body-1">
                        <li>Current BSIT 3rd Year, Caraga State University - Main (2022-2026)</li>
                        <li>Agusan National High School Senior High School, with honors (2020-2022)</li>
                        <li>Agusan National High School, with honors (2017-2020)</li>
                      </ul>
                    </v-col>
                  </v-row>
                </v-card-text>
              </v-card>
            </v-col>
          </v-row>
        </section>

        <section id="skills" class="my-16">
          <h2 class="text-h3 mb-6 text-center">Skills</h2>
          <v-row>
            <v-col v-for="skill in skills" :key="skill.name" cols="12" sm="6" md="4">
              <v-card :color="theme === 'light' ? 'beige-lighten-4' : 'beige-darken-4'" class="mx-auto" max-width="400">
                <v-card-text class="text-center">
                  <v-icon size="64" :color="theme === 'light' ? 'primary' : 'beige'">{{ skill.icon }}</v-icon>
                  <h3 class="text-h5 mt-4">{{ skill.name }}</h3>
                  <p>{{ skill.description }}</p>
                  <v-progress-linear
                    :model-value="skill.percentage"
                    :color="theme === 'light' ? 'primary' : 'beige'"
                    height="25"
                  >
                    <template v-slot:default="{ value }">
                      <strong :class="theme === 'dark' ? 'black--text' : ''">{{ Math.ceil(value) }}%</strong>
                    </template>
                  </v-progress-linear>
                </v-card-text>
              </v-card>
            </v-col>
          </v-row>
        </section>

        <section id="services" class="my-16">
          <h2 class="text-h3 mb-6 text-center">Services</h2>
          <v-row>
            <v-col v-for="service in services" :key="service.name" cols="12" sm="6" md="4">
              <v-card :color="theme === 'light' ? 'beige-lighten-4' : 'beige-darken-4'" class="mx-auto" max-width="400">
                <v-card-text class="text-center">
                  <v-icon size="64" :color="theme === 'light' ? 'primary' : 'beige'">{{ service.icon }}</v-icon>
                  <h3 class="text-h5 mt-4">{{ service.name }}</h3>
                  <p>{{ service.description }}</p>
                </v-card-text>
              </v-card>
            </v-col>
          </v-row>
        </section>

        <section id="projects" class="my-16">
          <h2 class="text-h3 mb-6 text-center">Projects</h2>
          <v-slide-group show-arrows>
            <v-slide-item v-for="project in projects" :key="project.name">
              <v-card :color="theme === 'light' ? 'beige-lighten-4' : 'beige-darken-4'" class="ma-4" width="600">
                <v-img :src="project.image" height="250" cover></v-img>
                <v-card-title>{{ project.name }}</v-card-title>
                <v-card-text>
                  <p>{{ project.description }}</p>
                </v-card-text>
                <v-card-actions>
                  <v-btn :color="theme === 'light' ? 'primary' : 'beige'" :href="project.link" target="_blank">
                    View Project
                  </v-btn>
                </v-card-actions>
              </v-card>
            </v-slide-item>
          </v-slide-group>
        </section>

        <section id="contact" class="my-16">
          <h2 class="text-h3 mb-6 text-center">Contact Me</h2>
          <v-row justify="center">
            <v-col cols="12" md="6">
              <v-card :color="theme === 'light' ? 'beige-lighten-4' : 'beige-darken-4'">
                <v-card-text>
                  <v-form @submit.prevent="submitForm">
                    <v-text-field v-model="form.name" label="Name" required></v-text-field>
                    <v-text-field v-model="form.email" label="Email" type="email" required></v-text-field>
                    <v-text-field v-model="form.subject" label="Subject" required></v-text-field>
                    <v-textarea v-model="form.message" label="Message" required></v-textarea>
                    <v-btn type="submit" :color="theme === 'light' ? 'primary' : 'beige'" block large>Send Message</v-btn>
                  </v-form>
                </v-card-text>
              </v-card>
            </v-col>
            <v-col cols="12" md="6">
              <v-card :color="theme === 'light' ? 'beige-lighten-4' : 'beige-darken-4'">
                <v-card-text>
                  <h3 class="text-h5 mb-4">Contact Information</h3>
                  <v-list>
                    <v-list-item>
                      <template v-slot:prepend>
                        <v-icon :color="theme === 'light' ? 'primary' : 'beige'">mdi-phone</v-icon>
                      </template>
                      <v-list-item-title>+63 930 0618 270</v-list-item-title>
                    </v-list-item>
                    <v-list-item>
                      <template v-slot:prepend>
                        <v-icon :color="theme === 'light' ? 'primary' : 'beige'">mdi-email</v-icon>
                      </template>
                      <v-list-item-title>aedrianberdijopuspus@gmail.com</v-list-item-title>
                    </v-list-item>
                    <v-list-item>
                      <template v-slot:prepend>
                        <v-icon :color="theme === 'light' ? 'primary' : 'beige'">mdi-map-marker</v-icon>
                      </template>
                      <v-list-item-title>Pob(21) Mahogany, Butuan City, Philippines</v-list-item-title>
                    </v-list-item>
                  </v-list>
                </v-card-text>
              </v-card>
              <v-card :color="theme === 'light' ? 'beige-lighten-4' : 'beige-darken-4'" class="mt-4">
                <v-card-text>
                  <h3 class="text-h5 mb-4">Location</h3>
                  <div class="google-map">
                    <iframe
                      src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3944.6441796309!2d125.54508331478395!3d8.958444993791!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x0%3A0x0!2zOMKwNTcnMzIuNCJOIDEyNcKwMzInNTIuMyJF!5e0!3m2!1sen!2sph!4v1635000000000!5m2!1sen!2sph"
                      width="100%"
                      height="300"
                      style="border:0;"
                      allowfullscreen=""
                      loading="lazy"
                    ></iframe>
                  </div>
                </v-card-text>
              </v-card>
            </v-col>
          </v-row>
          <v-row justify="center" class="mt-8">
            <v-col cols="auto">
              <v-btn icon href="https://www.facebook.com/kirito.puspus" target="_blank" :color="theme === 'light' ? 'primary' : 'beige'">
                <v-icon>mdi-facebook</v-icon>
              </v-btn>
            </v-col>
            <v-col cols="auto">
              <v-btn icon href="https://instagram.com/yanyan_senpai" target="_blank" :color="theme === 'light' ? 'primary' : 'beige'">
                <v-icon>mdi-instagram</v-icon>
              </v-btn>
            </v-col>
            <v-col cols="auto">
              <v-btn icon href="https://twitter.com/aedrianpuspus" target="_blank" :color="theme === 'light' ? 'primary' : 'beige'">
                <v-icon>mdi-twitter</v-icon>
              </v-btn>
            </v-col>
          </v-row>
        </section>
      </v-container>
    </v-main>

    <v-footer :color="theme === 'light' ? 'grey-lighten-2' : 'grey-darken-4'" padless>
      <v-container>
        <v-row justify="center" no-gutters>
          <v-col class="text-center" cols="12">
            {{ new Date().getFullYear() }} — <strong>Aedrian Puspus</strong>
          </v-col>
        </v-row>
      </v-container>
    </v-footer>

    <v-btn
      fab
      bottom
      right
      fixed
      @click="scrollToTop"
      :color="theme === 'light' ?   'primary' : 'beige'"
    >
      <v-icon>mdi-chevron-up</v-icon>
    </v-btn>
  </v-app>
</template>

<script>
export default {
  name: 'App',
  data: () => ({
    theme: 'dark',
    drawer: false,
    showDesignation: false,
    menuItems: [
      { title: 'Home', icon: 'mdi-home', href: '#home' },
      { title: 'About', icon: 'mdi-account', href: '#about' },
      { title: 'Skills', icon: 'mdi-lightbulb', href: '#skills' },
      { title: 'Services', icon: 'mdi-briefcase-outline', href: '#services' },
      { title: 'Projects', icon: 'mdi-briefcase', href: '#projects' },
      { title: 'Contact', icon: 'mdi-email', href: '#contact' },
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
      { name: 'Text-based Game', image: require('@/assets/text-based.png'), description: 'An interactive narrative adventure game played through text commands', link: '#' },
      { name: 'Simple Calculator', image: require('@/assets/calculator.png'), description: 'A user-friendly calculator application with basic arithmetic operations', link: '#' },
      { name: 'Portfolio Websites', image: require('@/assets/text-based.png'), description: 'Custom-designed portfolio websites to showcase professional work', link: '#' },
      { name: 'Weather App', image: require('@/assets/text-based.png'), description: 'A real-time weather application providing accurate forecasts', link: '#' },
      { name: 'To-Do List', image: require('@/assets/text-based.png'), description: 'A task management application to help organize daily activities', link: '#' },
    ],
    form: {
      name: '',
      email: '',
      subject: '',
      message: '',
    },
  }),
  methods: {
    submitForm() {
      console.log('Form submitted:', this.form);
      // Here we would typically send an email to seclet4ever@gmail.com
      console.log(`Sending email to seclet4ever@gmail.com`);
      console.log(`From: ${this.form.name} (${this.form.email})`);
      console.log(`Subject: ${this.form.subject}`);
      console.log(`Message: ${this.form.message}`);
      
      // Reset form after submission
      this.form = { name: '', email: '', subject: '', message: '' };
      alert('Thank you for your message! I will get back to you soon.');
    },
    toggleTheme() {
      this.theme = this.theme === 'light' ? 'dark' : 'light';
    },
    scrollToTop() {
      window.scrollTo({
        top: 0,
        behavior: 'smooth'
      });
    },
  },
  mounted() {
    setTimeout(() => {
      this.showDesignation = true;
    }, 500);
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

.v-list-item__content {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.black--text {
  color: black !important;
}
</style>
<template>
  <section id="home" class="my-8 my-md-16">
    <v-row align="center" justify="center">
      <v-col cols="12" md="6" class="text-center">
        <v-avatar size="150" size-md="200" class="mb-4">
          <v-img src="@/assets/avatar.jpg" alt="Aedrian Puspus"></v-img>
        </v-avatar>
        <h1 class="text-h4 text-md-h2 mt-4">Aedrian Puspus</h1>
        <v-slide-x-transition>
          <p class="text-body-1 text-md-h5 font-weight-light" v-show="showDesignation">Web Developer & Designer</p>
        </v-slide-x-transition>

        <v-btn :color="theme === 'light' ? 'primary' : 'beige'" class="mt-4 mr-2" href="#contact">Get in Touch</v-btn>
        <v-btn :color="theme === 'light' ? 'primary' : 'beige'" class="mt-4" :href="resumeUrl" download="Aedrian_Puspus_Resume.pdf">Download Resume</v-btn>
      </v-col>
    </v-row>
  </section>
</template>
  
  <script>
  export default {
    name: 'HomeSection',
    props: ['theme'],
    data: () => ({
      showDesignation: false,
      resumeUrl: '/YANYAN-RESUME-Final.pdf' // direct path to file in the public folder
    }),
    mounted() {
      setTimeout(() => {
        this.showDesignation = true;
      }, 500);
    }
  }
  </script>
  
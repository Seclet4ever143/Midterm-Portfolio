<template>
  <section id="home" class="my-8 my-md-16">
    <v-row align="center" justify="center">
      <v-col cols="12" md="6" class="text-center">
        <v-fade-transition>
          <v-avatar v-show="showAvatar" size="150" size-md="200" class="mb-4">
            <v-img src="@/assets/avatar.jpg" alt="Aedrian Puspus"></v-img>
          </v-avatar>
        </v-fade-transition>
        
        <v-slide-y-transition>
          <h1 v-show="showName" class="text-h4 text-md-h2 mt-4">Aedrian Puspus</h1>
        </v-slide-y-transition>
        
        <v-slide-x-transition>
          <p v-show="showDesignation" class="text-body-1 text-md-h5 font-weight-light">Web Developer & Designer</p>
        </v-slide-x-transition>

        <v-fade-transition>
          <div v-show="showButtons" class="mt-4">
            <v-btn :color="theme === 'light' ? 'primary' : 'beige'" class="mr-2" href="#contact">Get in Touch</v-btn>
            <v-btn :color="theme === 'light' ? 'primary' : 'beige'" :href="resumeUrl" download="Aedrian_Puspus_Resume.pdf">Download Resume</v-btn>
          </div>
        </v-fade-transition>
      </v-col>
    </v-row>
  </section>
</template>

<script>
export default {
  name: 'HomeSection',
  props: ['theme'],
  data: () => ({
    showAvatar: false,
    showName: false,
    showDesignation: false,
    showButtons: false,
    resumeUrl: '/YANYAN-RESUME-Final.pdf' // direct path to file in the public folder
  }),
  mounted() {
    this.animateContent();
  },
  methods: {
    animateContent() {
      setTimeout(() => { this.showAvatar = true; }, 100);
      setTimeout(() => { this.showName = true; }, 600);
      setTimeout(() => { this.showDesignation = true; }, 1100);
      setTimeout(() => { this.showButtons = true; }, 1600);
    }
  }
}
</script>

<style scoped>
.v-avatar {
  transition: transform 0.3s ease-in-out;
}

.v-avatar:hover {
  transform: scale(1.05);
}

.v-btn {
  transition: transform 0.2s ease-in-out;
}

.v-btn:hover {
  transform: translateY(-3px);
}
</style>
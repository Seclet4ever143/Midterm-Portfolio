<template>
  <section id="services" class="my-8 my-md-16">
    <v-fade-transition>
      <h2 v-show="showTitle" class="text-h5 text-md-h3 mb-6 text-center">Services</h2>
    </v-fade-transition>
    <v-row>
      <v-col v-for="(service, index) in services" :key="service.name" cols="12" sm="6" md="4">
        <v-scale-transition>
          <v-card 
            v-show="isServiceVisible(index)"
            :color="theme === 'light' ? 'beige-lighten-4' : 'beige-darken-4'" 
            class="mx-auto service-card" 
            max-width="400"
            elevation="2"
          >
            <v-card-text class="text-center pa-6">
              <v-icon size="48" size-md="64" :color="theme === 'light' ? 'primary' : 'beige'" class="service-icon mb-4 d-block mx-auto">
                {{ service.icon }}
              </v-icon>
              <h3 class="text-h6 text-md-h5 mb-4">{{ service.name }}</h3>
              <p class="text-body-2">{{ service.description }}</p>
              <v-btn 
                :color="theme === 'light' ? 'primary' : 'beige'" 
                variant="outlined" 
                class="mt-4"
                @click="scrollToSkills"
              >
                Learn More
              </v-btn>
            </v-card-text>
          </v-card>
        </v-scale-transition>
      </v-col>
    </v-row>
  </section>
</template>

<script>
export default {
  name: 'ServicesSection',
  props: ['theme', 'services'],
  data() {
    return {
      showTitle: false,
      visibleServices: 0,
    }
  },
  mounted() {
    this.animateContent()
  },
  methods: {
    animateContent() {
      setTimeout(() => { this.showTitle = true }, 100)
      this.services.forEach((_, index) => {
        setTimeout(() => {
          this.visibleServices++
        }, 500 + index * 200)
      })
    },
    isServiceVisible(index) {
      return index < this.visibleServices
    },
    learnMore(serviceName) {
      // This method can be implemented to show more details about the service
      console.log(`Learn more about ${serviceName}`)
      // You could emit an event here to be handled by a parent component
      this.$emit('learn-more', serviceName)
    },
    scrollToSkills() {
       const skillsSection = document.getElementById('skills');
       if (skillsSection) {
         skillsSection.scrollIntoView({ behavior: 'smooth' });
       }
     }
  }
}
</script>

<style scoped>
.service-card {
  transition: all 0.3s ease;
  height: 100%;
  display: flex;
  flex-direction: column;
}

.service-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.1) !important;
}

.service-card:hover .service-icon {
  transform: scale(1.1) rotate(10deg);
}

.service-icon {
  transition: transform 0.3s ease;
}

.v-card-text {
  flex-grow: 1;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}
</style>
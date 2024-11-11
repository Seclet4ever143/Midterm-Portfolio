<template>
  <section id="skills" class="my-8 my-md-16">
    <v-fade-transition>
      <h2 v-show="showTitle" class="text-h5 text-md-h3 mb-6 text-center">Skills</h2>
    </v-fade-transition>
    <v-row>
      <v-col v-for="(skill, index) in skills" :key="skill.name" cols="12" sm="6" md="4">
        <v-scale-transition>
          <v-card 
            v-show="isSkillVisible(index)"
            :color="theme === 'light' ? 'beige-lighten-4' : 'beige-darken-4'" 
            class="mx-auto skill-card" 
            max-width="400"
            elevation="2"
          >
            <v-card-text class="text-center">
              <v-icon size="48" size-md="64" :color="theme === 'light' ? 'primary' : 'beige'" class="skill-icon">
                {{ skill.icon }}
              </v-icon>
              <h3 class="text-h6 text-md-h5 mt-4">{{ skill.name }}</h3>
              <p>{{ skill.description }}</p>
              <v-progress-linear
                :model-value="animatedPercentage[index]"
                :color="theme === 'light' ? 'primary' : 'beige'"
                height="15"
                rounded
              >
                <template v-slot:default="{ value }">
                  <strong :class="theme === 'dark' ? 'black--text' : ''">{{ Math.ceil(value) }}%</strong>
                </template>
              </v-progress-linear>
            </v-card-text>
          </v-card>
        </v-scale-transition>
      </v-col>
    </v-row>
  </section>
</template>

<script>
export default {
  name: 'SkillsSection',
  props: ['theme', 'skills'],
  data() {
    return {
      showTitle: false,
      visibleSkills: 0,
      animatedPercentage: this.skills.map(() => 0),
    }
  },
  mounted() {
    this.animateContent()
  },
  methods: {
    animateContent() {
      setTimeout(() => { this.showTitle = true }, 100)
      this.skills.forEach((_, index) => {
        setTimeout(() => {
          this.visibleSkills++
          this.animatePercentage(index)
        }, 500 + index * 200)
      })
    },
    isSkillVisible(index) {
      return index < this.visibleSkills
    },
    animatePercentage(index) {
      const targetPercentage = this.skills[index].percentage
      const duration = 1500 // Animation duration in milliseconds
      const steps = 60 // Number of steps in the animation
      const increment = targetPercentage / steps
      let currentStep = 0

      const animation = setInterval(() => {
        if (currentStep < steps) {
          this.animatedPercentage[index] += increment
          currentStep++
        } else {
          this.animatedPercentage[index] = targetPercentage
          clearInterval(animation)
        }
      }, duration / steps)
    }
  }
}
</script>

<style scoped>
.skill-card {
  transition: all 0.3s ease;
  overflow: hidden;
}

.skill-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.1) !important;
}

.skill-card:hover .skill-icon {
  transform: scale(1.1);
}

.skill-icon {
  transition: transform 0.3s ease;
}

.v-progress-linear {
  border-radius: 15px;
  overflow: hidden;
}
</style>
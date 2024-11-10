<template>
  <section id="skills" class="my-8 my-md-16">
    <h2 class="text-h5 text-md-h3 mb-6 text-center">Skills</h2>
    <v-row>
      <v-col v-for="skill in skills" :key="skill.name" cols="12" sm="6" md="4">
        <v-card :color="theme === 'light' ? 'beige-lighten-4' : 'beige-darken-4'" class="mx-auto" max-width="400">
          <v-card-text class="text-center">
            <v-icon size="48" size-md="64" :color="theme === 'light' ? 'primary' : 'beige'">{{ skill.icon }}</v-icon>
            <h3 class="text-h6 text-md-h5 mt-4">{{ skill.name }}</h3>
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
</template>
  
  <script>
  export default {
    name: 'SkillsSection',
    props: ['theme', 'skills']
  }
  </script>
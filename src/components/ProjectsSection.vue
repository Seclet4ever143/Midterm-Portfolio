<template>
  <section id="projects" class="my-8 my-md-16">
    <h2 class="text-h5 text-md-h3 mb-6 text-center">Projects</h2>
    <v-slide-group show-arrows>
      <v-slide-item v-for="project in projects" :key="project.name">
        <v-card :color="theme === 'light' ? 'beige-lighten-4' : 'beige-darken-4'" class="ma-2 ma-md-4" width="500" width-md="300">
          <v-img :src="project.image" height="200" height-md="150" cover></v-img>
          <v-card-title class="text-subtitle-1 text-md-h6">{{ project.name }}</v-card-title>
          <v-card-text>
            <p class="text-caption text-md-body-2">{{ project.description }}</p>
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
</template>
  
  <script>
  export default {
    name: 'ProjectsSection',
    props: ['theme', 'projects']
  }
  </script>
<template>
  <section id="services" class="my-8 my-md-16">
    <h2 class="text-h5 text-md-h3 mb-6 text-center">Services</h2>
    <v-row>
      <v-col v-for="service in services" :key="service.name" cols="12" sm="6" md="4">
        <v-card :color="theme === 'light' ? 'beige-lighten-4' : 'beige-darken-4'" class="mx-auto" max-width="400">
          <v-card-text class="text-center">
            <v-icon size="48" size-md="64" :color="theme === 'light' ? 'primary' : 'beige'">{{ service.icon }}</v-icon>
            <h3 class="text-h6 text-md-h5 mt-4">{{ service.name }}</h3>
            <p>{{ service.description }}</p>
          </v-card-text>
        </v-card>
      </v-col>
    </v-row>
  </section>
</template>
  
  <script>
  export default {
    name: 'ServicesSection',
    props: ['theme', 'services']
  }
  </script>
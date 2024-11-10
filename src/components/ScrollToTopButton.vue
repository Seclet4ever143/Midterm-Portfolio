<template>
    <v-btn
      fab
      bottom
      right
      fixed
      @click="$emit('scroll-to-top')"
      :color="theme === 'light' ? 'primary' : 'beige'"
    >
      <v-icon>mdi-chevron-up</v-icon>
    </v-btn>
  </template>
  
  <script>
  export default {
    name: 'ScrollToTopButton',
    props: ['theme']
  }
  </script>
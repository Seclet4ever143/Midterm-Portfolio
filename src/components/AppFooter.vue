<template>
    <v-footer :color="theme === 'light' ? 'grey-lighten-2' : 'grey-darken-4'" padless>
      <v-container>
        <v-row justify="center" no-gutters>
          <v-col class="text-center" cols="12">
            {{ new Date().getFullYear() }} — <strong>Aedrian Puspus</strong>
          </v-col>
        </v-row>
      </v-container>
    </v-footer>
  </template>
  
  <script>
  export default {
    name: 'AppFooter',
    props: ['theme']
  }
  </script>
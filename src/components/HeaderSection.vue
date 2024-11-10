<template>
  <div>
    <v-app-bar app :color="theme === 'light' ? 'grey-lighten-2' : 'grey-darken-4'">
      <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>
      <v-toolbar-title>Aedrian Puspus | Web Developer</v-toolbar-title>
      <v-spacer></v-spacer>
      <v-btn icon @click="$emit('toggle-theme')">
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
      <v-container class="d-flex flex-column">
        <v-row justify="center" class="mt-5">
          <v-col cols="12" class="text-center">
            <v-avatar size="100">
              <v-img src="@/assets/logo.png" alt="Logo"></v-img>
            </v-avatar>
          </v-col>
        </v-row>
        <v-row class="flex-grow-1 text-center">
          <v-col cols="10">
            <v-list nav>
              <v-list-item v-for="(item, i) in menuItems" :key="i" :href="item.href" @click="closeDrawer" link>
                <template v-slot:prepend>
                  <v-icon>{{ item.icon }}</v-icon>
                </template>
                <v-list-item-title>{{ item.title }}</v-list-item-title>
              </v-list-item>
            </v-list>
          </v-col>
        </v-row>
        <v-row justify="center" class="mb-4">
          <v-col cols="12" class="text-center">
            <v-btn icon @click="$emit('toggle-theme')">
              <v-icon>{{ theme === 'light' ? 'mdi-weather-night' : 'mdi-weather-sunny' }}</v-icon>
            </v-btn>
          </v-col>
        </v-row>
      </v-container>
    </v-navigation-drawer>
  </div>
</template>

<script>
export default {
  name: 'HeaderSection',
  props: ['theme'],
  emits: ['toggle-theme'],
  data() {
    return {
      drawer: false,
      menuItems: [
        { title: 'Home', href: '#home', icon: 'mdi-home' },
        { title: 'About', href: '#about', icon: 'mdi-account' },
        { title: 'Education', href: '#education', icon: 'mdi-school' },
        { title: 'Skills', href: '#skills', icon: 'mdi-code-tags' },
        { title: 'Services', href: '#services', icon: 'mdi-briefcase' },
        { title: 'Projects', href: '#projects', icon: 'mdi-folder' },
        { title: 'Contact', href: '#contact', icon: 'mdi-email' },
      ],
    }
  },
  methods: {
    closeDrawer() {
      this.drawer = false
    }
  }
}
</script>
<template>
  <section id="contact" class="my-8 my-md-16">
    <h2 class="text-h5 text-md-h3 mb-6 text-center">Contact Me</h2>
    <v-row justify="center">
      <v-col cols="12" md="6">
        <v-card :color="theme === 'light' ? 'beige-lighten-4' : 'beige-darken-4'">
          <v-card-text>
            <v-form @submit.prevent="submitForm">
              <v-text-field v-model="form.name" label="Name" required></v-text-field>
              <v-text-field v-model="form.email" label="Email" type="email" required></v-text-field>
              <v-text-field v-model="form.subject" label="Subject" required></v-text-field>
              <v-textarea v-model="form.message" label="Message" required></v-textarea>
              <v-btn type="submit" :color="theme === 'light' ? 'primary' : 'beige'" block>Send Message</v-btn>
            </v-form>
          </v-card-text>
        </v-card>
      </v-col>
      <v-col cols="12" md="6">
        <v-card :color="theme === 'light' ? 'beige-lighten-4' : 'beige-darken-4'">
          <v-card-text>
            <h3 class="text-h6 mb-4">Contact Information</h3>
            <v-list>
              <v-list-item>
                <template v-slot:prepend>
                  <v-icon :color="theme === 'light' ? 'primary' : 'beige'">mdi-phone</v-icon>
                </template>
                <v-list-item-title>+63 930 0618 270</v-list-item-title>
              </v-list-item>
              <v-list-item>
                <template v-slot:prepend>
                  <v-icon :color="theme === 'light' ? 'primary' : 'beige'">mdi-email</v-icon>
                </template>
                <v-list-item-title>aedrianberdijopuspus@gmail.com</v-list-item-title>
              </v-list-item>
              <v-list-item>
                <template v-slot:prepend>
                  <v-icon :color="theme === 'light' ? 'primary' : 'beige'">mdi-map-marker</v-icon>
                </template>
                <v-list-item-title>Pob(21) Mahogany, Butuan City, Philippines</v-list-item-title>
              </v-list-item>
            </v-list>
          </v-card-text>
        </v-card>
        <v-card :color="theme === 'light' ? 'beige-lighten-4' : 'beige-darken-4'" class="mt-4">
          <v-card-text>
            <h3 class="text-h6 mb-4">Location</h3>
            <div class="google-map">
              <iframe
                src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3944.6441796309!2d125.54508331478395!3d8.958444993791!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x0%3A0x0!2zOMKwNTcnMzIuNCJOIDEyNcKwMzInNTIuMyJF!5e0!3m2!1sen!2sph!4v1635000000000!5m2!1sen!2sph"
                width="100%"
                height="200"
                style="border:0;"
                allowfullscreen=""
                loading="lazy"
              ></iframe>
            </div>
          </v-card-text>
        </v-card>
      </v-col>
    </v-row>
    <v-row justify="center" class="mt-8">
      <v-col cols="auto">
        <v-btn icon href="https://www.facebook.com/kirito.puspus" target="_blank" :color="theme === 'light' ? 'primary' : 'beige'">
          <v-icon>mdi-facebook</v-icon>
        </v-btn>
      </v-col>
      <v-col cols="auto">
        <v-btn icon href="https://www.instagram.com/an_reui/" target="_blank" :color="theme === 'light' ? 'primary' : 'beige'">
          <v-icon>mdi-instagram</v-icon>
        </v-btn>
      </v-col>
      <v-col cols="auto">
        <v-btn icon href="https://x.com/AeDriaNxD" target="_blank" :color="theme === 'light' ? 'primary' : 'beige'">
          <v-icon>mdi-twitter</v-icon>
        </v-btn>
      </v-col>
    </v-row>
  </section>
</template>
  
  <script>
  export default {
    name: 'ContactSection',
    props: ['theme'],
    data: () => ({
      form: {
        name: '',
        email: '',
        subject: '',
        message: '',
      },
    }),
    methods: {
      submitForm() {
        this.$emit('submit-form', this.form)
        this.form = { name: '', email: '', subject: '', message: '' }
      }
    }
  }
  </script>
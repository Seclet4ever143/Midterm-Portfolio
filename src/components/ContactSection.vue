<template>
  <section id="contact" class="my-8 my-md-16">
    <v-fade-transition>
      <h2 v-show="showTitle" class="text-h5 text-md-h3 mb-6 text-center">Contact Me</h2>
    </v-fade-transition>
    <v-row justify="center">
      <v-col cols="12" md="6">
        <v-scale-transition>
          <v-card v-show="showForm" :color="theme === 'light' ? 'beige-lighten-4' : 'beige-darken-4'" class="contact-card">
            <v-card-text>
              <v-form @submit.prevent="submitForm">
                <v-text-field 
                  v-model="form.name" 
                  label="Name" 
                  required
                  :color="theme === 'light' ? 'primary' : 'beige'"
                  class="input-field"
                ></v-text-field>
                <v-text-field 
                  v-model="form.email" 
                  label="Email" 
                  type="email" 
                  required
                  :color="theme === 'light' ? 'primary' : 'beige'"
                  class="input-field"
                ></v-text-field>
                <v-text-field 
                  v-model="form.subject" 
                  label="Subject" 
                  required
                  :color="theme === 'light' ? 'primary' : 'beige'"
                  class="input-field"
                ></v-text-field>
                <v-textarea 
                  v-model="form.message" 
                  label="Message" 
                  required
                  :color="theme === 'light' ? 'primary' : 'beige'"
                  class="input-field"
                ></v-textarea>
                <v-btn 
                  type="submit" 
                  :color="theme === 'light' ? 'primary' : 'beige'" 
                  block
                  class="submit-btn"
                >Send Message</v-btn>
              </v-form>
            </v-card-text>
          </v-card>
        </v-scale-transition>
      </v-col>
      <v-col cols="12" md="6">
        <v-scale-transition>
          <v-card v-show="showInfo" :color="theme === 'light' ? 'beige-lighten-4' : 'beige-darken-4'" class="contact-card">
            <v-card-text>
              <h3 class="text-h6 mb-4">Contact Information</h3>
              <v-list>
                <v-list-item v-for="(item, index) in contactInfo" :key="index" class="contact-item">
                  <template v-slot:prepend>
                    <v-icon :color="theme === 'light' ? 'primary' : 'beige'" class="contact-icon">{{ item.icon }}</v-icon>
                  </template>
                  <v-list-item-title>{{ item.text }}</v-list-item-title>
                </v-list-item>
              </v-list>
            </v-card-text>
          </v-card>
        </v-scale-transition>
        <v-scale-transition>
          <v-card v-show="showMap" :color="theme === 'light' ? 'beige-lighten-4' : 'beige-darken-4'" class="mt-4 contact-card">
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
        </v-scale-transition>
      </v-col>
    </v-row>
    <v-row justify="center" class="mt-8">
      <v-col v-for="(social, index) in socialLinks" :key="index" cols="auto">
        <v-scale-transition>
          <v-btn 
            v-show="showSocial"
            icon 
            :href="social.link" 
            target="_blank" 
            :color="theme === 'light' ? 'primary' : 'beige'"
            class="social-btn"
          >
            <v-icon>{{ social.icon }}</v-icon>
          </v-btn>
        </v-scale-transition>
      </v-col>
    </v-row>
  </section>
</template>

<script>
export default {
  name: 'ContactSection',
  props: ['theme'],
  data: () => ({
    showTitle: false,
    showForm: false,
    showInfo: false,
    showMap: false,
    showSocial: false,
    form: {
      name: '',
      email: '',
      subject: '',
      message: '',
    },
    contactInfo: [
      { icon: 'mdi-phone', text: '+63 930 0618 270' },
      { icon: 'mdi-email', text: 'aedrianberdijopuspus@gmail.com' },
      { icon: 'mdi-map-marker', text: 'Pob(21) Mahogany, Butuan City, Philippines' },
    ],
    socialLinks: [
      { icon: 'mdi-facebook', link: 'https://www.facebook.com/kirito.puspus' },
      { icon: 'mdi-instagram', link: 'https://www.instagram.com/an_reui/' },
      { icon: 'mdi-twitter', link: 'https://x.com/AeDriaNxD' },
    ],
  }),
  mounted() {
    this.animateContent();
  },
  methods: {
    submitForm() {
      this.$emit('submit-form', this.form)
      this.form = { name: '', email: '', subject: '', message: '' }
    },
    animateContent() {
      setTimeout(() => { this.showTitle = true }, 100);
      setTimeout(() => { this.showForm = true }, 300);
      setTimeout(() => { this.showInfo = true }, 500);
      setTimeout(() => { this.showMap = true }, 700);
      setTimeout(() => { this.showSocial = true }, 900);
    }
  }
}
</script>

<style scoped>
.contact-card {
  transition: all 0.3s ease;
  overflow: hidden;
}

.contact-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.1) !important;
}

.input-field {
  transition: all 0.3s ease;
}

.input-field:hover, .input-field:focus {
  transform: translateY(-2px);
}

.submit-btn {
  transition: all 0.3s ease;
}

.submit-btn:hover {
  transform: translateY(-2px);
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
}

.contact-item {
  transition: all 0.3s ease;
}

.contact-item:hover {
  background-color: rgba(0, 0, 0, 0.05);
}

.contact-icon {
  transition: transform 0.3s ease;
}

.contact-item:hover .contact-icon {
  transform: scale(1.2);
}

.social-btn {
  transition: all 0.3s ease;
}

.social-btn:hover {
  transform: translateY(-3px) scale(1.1);
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
}

.google-map {
  transition: all 0.3s ease;
}

.google-map:hover {
  transform: scale(1.02);
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
}
</style>
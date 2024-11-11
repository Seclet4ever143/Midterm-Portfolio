<template>
  <section id="certificates" class="my-8 my-md-16">
    <v-fade-transition>
      <h2 v-show="showTitle" class="text-h5 text-md-h3 mb-6 text-center">Certificates</h2>
    </v-fade-transition>
    <v-slide-group show-arrows>
      <v-slide-item v-for="(certificate, index) in certificates" :key="certificate.name">
        <v-scale-transition>
          <v-card 
            v-show="isCertificateVisible(index)"
            :color="theme === 'light' ? 'beige-lighten-4' : 'beige-darken-4'" 
            class="ma-2 ma-md-4 certificate-card" 
            width="300"
          >
            <div class="certificate-image-container">
              <v-img :src="certificate.image" height="200" cover class="certificate-image"></v-img>
              <div class="certificate-overlay">
                <v-btn 
                  :color="theme === 'light' ? 'primary' : 'beige'" 
                  :href="certificate.link" 
                  target="_blank"
                  class="certificate-btn"
                >
                  View Certificate
                </v-btn>
              </div>
            </div>
            <v-card-title class="text-subtitle-1 text-md-h6">{{ certificate.name }}</v-card-title>
            <v-card-text>
              <p class="text-caption text-md-body-2">{{ certificate.issuer }}</p>
              <p class="text-caption text-md-body-2">{{ certificate.date }}</p>
            </v-card-text>
          </v-card>
        </v-scale-transition>
      </v-slide-item>
    </v-slide-group>
  </section>
</template>

<script>
export default {
  name: 'CertificateSection',
  props: {
    theme: {
      type: String,
      required: true
    },
    certificates: {
      type: Array,
      required: true
    }
  },
  data() {
    return {
      showTitle: false,
      visibleCertificates: 0
    }
  },
  mounted() {
    this.animateContent()
  },
  methods: {
    animateContent() {
      setTimeout(() => { this.showTitle = true }, 100)
      this.certificates.forEach((_, index) => {
        setTimeout(() => {
          this.visibleCertificates++
        }, 500 + index * 200)
      })
    },
    isCertificateVisible(index) {
      return index < this.visibleCertificates
    }
  }
}
</script>

<style scoped>
.certificate-card {
  transition: all 0.3s ease;
  overflow: hidden;
}

.certificate-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.1) !important;
}

.certificate-image-container {
  position: relative;
  overflow: hidden;
}

.certificate-image {
  transition: transform 0.3s ease;
}

.certificate-card:hover .certificate-image {
  transform: scale(1.05);
}

.certificate-overlay {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: rgba(0, 0, 0, 0.5);
  display: flex;
  align-items: center;
  justify-content: center;
  opacity: 0;
  transition: opacity 0.3s ease;
}

.certificate-card:hover .certificate-overlay {
  opacity: 1;
}

.certificate-btn {
  transform: translateY(20px);
  transition: all 0.3s ease;
}

.certificate-card:hover .certificate-btn {
  transform: translateY(0);
}

.v-card-title, .v-card-text {
  transition: color 0.3s ease;
}

.certificate-card:hover .v-card-title {
  color: var(--v-primary-base);
}
</style>
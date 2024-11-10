<template>
  <section id="about" class="my-8 my-md-16">
    <v-row justify="center">
      <v-col cols="12" md="10">
        <v-card :color="theme === 'light' ? 'beige-lighten-4' : 'beige-darken-4'">
          <v-card-title class="text-h5 text-md-h3 text-center">About Me</v-card-title>
          <v-card-text>
            <v-row align="center">
              <v-col cols="12" md="4" class="text-center mb-6 mb-md-0">
                <v-avatar size="150" size-md="250" class="elevation-5">
                  <v-img src="@/assets/AboutMe.png" alt="Aedrian Puspus"></v-img>
                </v-avatar>
              </v-col>
              <v-col cols="12" md="8">
                <p class="text-body-2 text-justify">Hello! I'm Aedrian Puspus, a third-year BSIT student at Caraga State University with a deep passion for web development and a constant drive to learn and grow in this ever-evolving field. Over the years, my journey into coding has been both challenging and rewarding, fueling my ambition to create dynamic, user-centered websites that blend functionality with aesthetic appeal.</p>
                <br>
                <p class="text-body-2 text-justify">As an aspiring web developer, I'm committed to designing seamless digital experiences that are both accessible and visually engaging. I thrive on challenges, continually seeking new opportunities to push my skills and stay updated with the latest industry trends. For me, coding is more than just a skill; it's a creative outlet and a way to bring impactful ideas to life.</p>
                <br>
                <p class="text-body-2 text-justify">With an unwavering dedication to continuous learning, I'm excited about the boundless possibilities in web development and eager to contribute to meaningful projects. Let's build something remarkable together!</p>
              </v-col> 
            </v-row>
          </v-card-text>
        </v-card>
      </v-col>
    </v-row>
  </section>
</template>

<script>
export default {
    name: 'AboutSection',
    props: ['theme']
}
</script>
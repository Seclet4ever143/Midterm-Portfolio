<template>
  <v-container fluid>
    <v-row class="text-center my-4">
      <v-col cols="12">
        <h2 class="text-h4">Education</h2>
        <v-divider class="my-4"></v-divider>
      </v-col>
    </v-row>

    <!-- Timeline -->
    <div class="timeline-container">
      <div class="timeline-line"></div>
      <div v-for="(item, index) in education" :key="index" class="timeline-item">
        <div class="timeline-dot"></div>
        <div class="timeline-content">
          <v-card outlined class="timeline-card">
            <v-card-title class="timeline-card-title">
              <span>{{ item.school }}</span>
            </v-card-title>
            <v-card-subtitle>{{ item.description }}</v-card-subtitle>
            <v-card-text>{{ item.year }}</v-card-text>

            <!-- Achievements -->
            <v-chip-group column class="my-2" dense>
              <v-chip v-for="(achievement, i) in item.achievements" :key="i" color="primary" text-color="white"
                class="ma-1" outlined>
                {{ achievement }}
              </v-chip>
            </v-chip-group>
          </v-card>
        </div>
      </div>
    </div>
  </v-container>
</template>

<script>
export default {
  name: 'EducationSection',
  data() {
    return {
      education: [
        {
          year: '2021 - Present',
          degree: 'Bachelor of Science in Information Technology (BSIT)',
          school: 'Caraga State University',
          description: `Currently pursuing a degree in Information Technology, specializing in web development and software engineering.`,
          achievements: ['Dean\'s Lister (Ongoing)', 'Web Development Project Leader'],
        },
        {
          year: '2018 - 2020',
          degree: 'Senior High School',
          school: 'Agusan National High Senior High School',
          description: `STEM strand focusing on Computer Science electives, including HTML, CSS, JavaScript, and web development.`,
          achievements: ['Honor Student'],
        },
      ]



    };
  },
};
</script>

<style scoped>
.timeline-container {
  position: relative;
  padding: 0 15px;
}

.timeline-line {
  position: absolute;
  width: 4px;
  background-color: #3f51b5;
  /* Primary color line */
  top: 0;
  bottom: 0;
  left: 20px;
  z-index: 0;
}

.timeline-item {
  display: flex;
  margin-bottom: 16px;
  align-items: center;
  position: relative;
}

.timeline-dot {
  position: absolute;
  left: 0;
  width: 16px;
  height: 16px;
  border-radius: 50%;
  background-color: #3f51b5;
  /* Primary color dot */
  border: 2px solid white;
  z-index: 1;
}

.timeline-content {
  margin-left: 30px;
  /* Space between the dot and content */
  z-index: 1;
}

.timeline-card {
  width: 100%;
  transition: all 0.3s ease;
}

.timeline-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

/* Responsiveness */
@media (max-width: 600px) {
  .timeline-container {
    padding: 0;
  }

  .timeline-item {
    flex-direction: column;
    align-items: flex-start;
    margin-bottom: 24px;
  }

  .timeline-dot {
    margin-left: 0;
    margin-bottom: 10px;
  }

  .timeline-content {
    margin-left: 0;
    padding-left: 0;
    width: 100%;
  }

  .timeline-card-title {
    font-size: 1rem;
  }

  .timeline-card-subtitle {
    font-size: 0.9rem;
  }

  .timeline-card-text {
    font-size: 0.9rem;
  }

  .v-chip {
    font-size: 0.75rem;
  }
}
</style>

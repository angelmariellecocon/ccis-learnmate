<script setup>
import WelcomeWidget from '@/components/system/dashboard/WelcomeWidget.vue'
import AppLayout from '@/components/layout/AppLayout.vue'

import { useDisplay } from 'vuetify'
import { ref } from 'vue'

// Use Pinia Store and Router

// Utilize pre-defined vue functions
const { mobile } = useDisplay()

// Load Variables
const isDrawerVisible = ref(!mobile.value)
const theme = ref(localStorage.getItem('theme') ?? 'light')

// Check user role and redirect if necessary

// Toggle drawer
const toggleDrawer = () => {
  isDrawerVisible.value = !isDrawerVisible.value
}

// On Theme Update
const onThemeUpdate = (value) => {
  theme.value = value
}
</script>

<template>
  <AppLayout
    :is-with-app-bar-nav-icon="true"
    :transparent="true"
    @is-drawer-visible="toggleDrawer"
    @theme="onThemeUpdate"
  >
    <template #content>
      <v-container fluid class="about-container py-10">
        <v-row>
          <!-- Tutee View Only -->
          <v-col cols="12">
            <WelcomeWidget :theme="theme"></WelcomeWidget>
          </v-col>
          <!-- Add more tutee specific components here -->

          <v-card elevation="2" class="pa-6 about-card">
            <v-row>
              <v-col cols="12" md="8">
                <h1 class="text-h4 font-weight-bold mb-4 deep-purple--text text--darken-2">
                  About LearnMate
                </h1>
                <p class="text-body-1 mb-4">
                  LearnMate is a student-first academic support platform designed to simplify and
                  personalize your learning journey. We bring students and tutors together in a
                  secure, easy-to-use environment that supports meaningful learning and real
                  academic improvements.
                </p>

                <p class="text-body-1 mb-4">
                  Whether you're struggling with a challenging subject, preparing for exams, or just
                  need consistent academic support, LearnMate helps match you with the right tutor
                  based on your subject needs, schedule, and learning preferences. From booking
                  sessions to reviewing study progress, everything is centralized in one dashboard.
                </p>

                <p class="text-body-1">
                  Our mission is to empower learners of all levels by making education accessible,
                  organized, and engaging. With tools for session tracking, resource sharing, and
                  real-time communication, LearnMate helps create a connected and goal-driven
                  learning experience for every student.
                </p>
              </v-col>

              <v-col cols="12" md="4" class="d-flex align-center justify-center mb-6 mb-md-0">
                <v-img
                  src="/images/learnmate-logo.png"
                  width="100%"
                  max-width="250"
                  alt="LearnMate Logo"
                ></v-img>
              </v-col>
            </v-row>
          </v-card>
        </v-row>
      </v-container>
    </template>
  </AppLayout>
</template>

<style scoped>
.about-container {
  background: #fefefe;
}

.about-card {
  background: #fffdf4;
  border-radius: 16px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.08);
}

.text-body-1 {
  color: #546e7a;
  line-height: 1.7;
}
</style>

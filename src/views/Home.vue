<template>
  <div class="home-page">
    <Hero />
    <PilotWorks />
    <WhyMe />
    <MyCV />
    <ContactForm />
    <Footer />
  </div>
</template>

<script setup lang="ts">
import Hero from '../components/Hero.vue'
import PilotWorks from '../components/PilotWorks.vue'
import WhyMe from '../components/WhyMe.vue'
import MyCV from '../components/MyCV.vue'
import ContactForm from '../components/ContactForm.vue'
import Footer from '../components/Footer.vue'
</script>

<style scoped>
.home-page {
  min-height: 100vh;
}
</style>
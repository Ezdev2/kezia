<template>
  <div class="home-page">
    <div class="noise-overlay"></div>
    
    <div class="content-wrapper">
      <Hero />
      <PilotWorks />
      <WhyMe />
      <MyCV />
      <ContactForm />
      <Footer />
    </div>
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
  position: relative;
  background-color: #0b0e14;
  background-image: url("../assets/bg.svg");
  background-attachment: fixed;
  background-size: cover;
  overflow-x: hidden;
}

/* Overlay */
.home-page::before {
  content: "";
  position: absolute;
  inset: 0;
  background: rgba(11, 14, 20, 0.8);
  z-index: 0;
}

/* Contenu au-dessus */
.home-page > * {
  position: relative;
  z-index: 1;
}


.noise-overlay {
  position: absolute;
  inset: 0;
  width: 100%;
  height: 100%;
  opacity: 0.04;
  z-index: 1;
  pointer-events: none;
  background-image: url('https://grainy-gradients.vercel.app/noise.svg');
}

.content-wrapper {
  position: relative;
  z-index: 2;
}
</style>
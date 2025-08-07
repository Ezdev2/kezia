<template>
  <div id="app" class="app">
    <Navbar />
    <router-view />
  </div>
</template>

<script setup lang="ts">
import { onMounted } from 'vue'
import Navbar from './components/Navbar.vue'
import { gsap } from 'gsap'
import { ScrollTrigger } from 'gsap/ScrollTrigger'

gsap.registerPlugin(ScrollTrigger)

onMounted(() => {
  // Global scroll animations setup
  gsap.utils.toArray('.animate-on-scroll').forEach((elem: any) => {
    gsap.fromTo(elem, 
      { opacity: 0, y: 50 },
      {
        opacity: 1,
        y: 0,
        duration: 0.8,
        scrollTrigger: {
          trigger: elem,
          start: 'top 85%',
          end: 'bottom 15%',
          toggleActions: 'play none none reverse'
        }
      }
    )
  })
})
</script>

<style>
.app {
  background: linear-gradient(135deg, #1a1a2e 0%, #16213e 50%, #1a1a2e 100%);
  min-height: 100vh;
  color: #ffffff;
}
</style>
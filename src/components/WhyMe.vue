<template>
  <section id="why-me" class="why-me-section section">
    <div class="container">
      <div class="section-header" data-aos="fade-up">
        <h2 class="section-title">Why Choose Me?</h2>
        <p class="section-subtitle">What sets me apart in the design world</p>
      </div>

      <div class="qualities-grid">
        <div 
          v-for="(quality, index) in qualities" 
          :key="quality.id"
          class="quality-card"
          :data-aos="getAnimation(index)"
          :data-aos-delay="index * 150"
        >
          <div class="quality-icon">
            <div v-html="quality.icon"></div>
          </div>
          <h3 class="quality-title">{{ quality.title }}</h3>
          <p class="quality-description">{{ quality.description }}</p>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { ref } from 'vue'

interface Quality {
  id: number
  title: string
  description: string
  icon: string
}

const qualities = ref<Quality[]>([
  {
    id: 1,
    title: "Professionalism",
    description: "I deliver high-quality work on time, maintain clear communication throughout projects, and always exceed client expectations with attention to detail.",
    icon: `<svg width="48" height="48" viewBox="0 0 24 24" fill="none">
      <path d="M21 15A2 2 0 0 1 19 17H7L4 20V6A2 2 0 0 1 6 4H19A2 2 0 0 1 21 6V15Z" stroke="url(#gradient4)" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
      <defs>
        <linearGradient id="gradient4" x1="0%" y1="0%" x2="100%" y2="100%">
          <stop offset="0%" style="stop-color:#a855f7"/>
          <stop offset="100%" style="stop-color:#f472b6"/>
        </linearGradient>
      </defs>
    </svg>`
  },
  {
    id: 2,
    title: "Creativity in Design",
    description: "I bring fresh perspectives and innovative solutions to every project, blending artistic vision with user-centered design principles.",
    icon: `<svg width="48" height="48" viewBox="0 0 24 24" fill="none">
      <path d="M12 2L2 7L12 12L22 7L12 2Z" stroke="url(#gradient2)" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
      <path d="M2 17L12 22L22 17" stroke="url(#gradient2)" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
      <path d="M2 12L12 17L22 12" stroke="url(#gradient2)" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
      <defs>
        <linearGradient id="gradient2" x1="0%" y1="0%" x2="100%" y2="100%">
          <stop offset="0%" style="stop-color:#a855f7"/>
          <stop offset="100%" style="stop-color:#f472b6"/>
        </linearGradient>
      </defs>
    </svg>`
  },
  {
    id: 3,
    title: "Efficiency",
    description: "I optimize workflows and use cutting-edge tools to deliver exceptional results faster, without compromising on quality or creativity.",
    icon: `<svg width="48" height="48" viewBox="0 0 24 24" fill="none">
      <path d="M13 2L3 14H12L11 22L21 10H12L13 2Z" stroke="url(#gradient3)" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
      <defs>
        <linearGradient id="gradient3" x1="0%" y1="0%" x2="100%" y2="100%">
          <stop offset="0%" style="stop-color:#a855f7"/>
          <stop offset="100%" style="stop-color:#f472b6"/>
        </linearGradient>
      </defs>
    </svg>`
  }
])

const getAnimation = (index: number): string => {
  const animations = ['fade-up', 'fade-down', 'fade-right', 'fade-left']
  return animations[index % animations.length]
}
</script>

<style scoped>
.why-me-section {
  background: var(--primary-bg);
}

.section-header {
  text-align: center;
  margin-bottom: 4rem;
}

.section-title {
  margin-bottom: 1rem;
  color: var(--text-primary);
}

.section-subtitle {
  font-size: 1.2rem;
  color: var(--text-muted);
  max-width: 600px;
  margin: 0 auto;
}

.qualities-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 2rem;
}

.quality-card {
  background: var(--gradient-card);
  border-radius: 1.5rem;
  padding: 2.5rem;
  text-align: center;
  border: 1px solid var(--border-color);
  transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
  backdrop-filter: blur(10px);
  position: relative;
  overflow: hidden;
}

.quality-card:hover {
  transform: translateY(-8px);
  box-shadow: var(--shadow-primary);
  border-color: var(--primary-purple);
}

.quality-card::before {
  content: '';
  position: absolute;
  top: -50%;
  left: -50%;
  width: 200%;
  height: 200%;
  background: conic-gradient(from 0deg, transparent, var(--primary-purple), transparent);
  opacity: 0;
  transition: opacity 0.3s ease;
  animation: rotate 4s linear infinite;
}

.quality-card:hover::before {
  opacity: 0.1;
}

.quality-icon {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 80px;
  height: 80px;
  background: var(--gradient-card);
  border: 2px solid var(--border-color);
  border-radius: 50%;
  margin: 0 auto 1.5rem;
  position: relative;
  z-index: 2;
  transition: all 0.3s ease;
}

.quality-card:hover .quality-icon {
  border-color: var(--primary-purple);
  transform: scale(1.1);
}

.quality-title {
  font-size: 1.5rem;
  font-weight: 600;
  color: var(--text-primary);
  margin-bottom: 1rem;
  position: relative;
  z-index: 2;
}

.quality-description {
  color: var(--text-secondary);
  line-height: 1.7;
  position: relative;
  z-index: 2;
}

@keyframes rotate {
  from { transform: rotate(0deg); }
  to { transform: rotate(360deg); }
}

@media (max-width: 768px) {
  .qualities-grid {
    grid-template-columns: 1fr;
    gap: 1.5rem;
  }

  .quality-card {
    padding: 2rem;
  }

  .quality-icon {
    width: 64px;
    height: 64px;
    margin-bottom: 1rem;
  }

  .quality-title {
    font-size: 1.25rem;
  }
}
</style>
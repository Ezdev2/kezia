<template>
  <section id="works" class="pilot-works-section section">
    <div class="container">
      <div class="section-header" data-aos="fade-up">
        <h2 class="section-title">Pilot Works</h2>
        <p class="section-subtitle">A showcase of my featured design projects</p>
      </div>

      <div class="works-grid">
        <div 
          v-for="(work, index) in pilotWorks" 
          :key="work.id"
          class="work-card"
          :data-aos="index % 2 === 0 ? 'fade-right' : 'fade-left'"
          :data-aos-delay="index * 100"
        >
          <div class="work-image">
            <img :src="work.image" :alt="work.title" />
            <div class="work-overlay">
              <a :href="work.link" target="_blank" class="visit-btn">
                <svg width="24" height="24" viewBox="0 0 24 24" fill="none">
                  <path d="M7 17L17 7M17 7H7M17 7V17" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                </svg>
                Visit
              </a>
            </div>
          </div>
          <div class="work-content">
            <h3 class="work-title">{{ work.title }}</h3>
            <p class="work-category">{{ work.category }}</p>
          </div>
        </div>
      </div>

      <div class="section-footer" data-aos="fade-up" data-aos-delay="600">
        <router-link to="/works" class="btn btn-outline">
          View All Projects
          <svg width="20" height="20" viewBox="0 0 24 24" fill="none">
            <path d="M5 12h14M12 5l7 7-7 7" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
          </svg>
        </router-link>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { ref } from 'vue'

interface PilotWork {
  id: number
  title: string
  category: string
  image: string
  link: string
}

const pilotWorks = ref<PilotWork[]>([
  {
    id: 1,
    title: "E-commerce Mobile App",
    category: "Mobile Design",
    image: "https://images.pexels.com/photos/196644/pexels-photo-196644.jpeg?auto=compress&cs=tinysrgb&w=600",
    link: "#"
  },
  {
    id: 2,
    title: "Financial Dashboard",
    category: "Web Design",
    image: "https://images.pexels.com/photos/265087/pexels-photo-265087.jpeg?auto=compress&cs=tinysrgb&w=600",
    link: "#"
  },
  {
    id: 3,
    title: "Brand Identity Design",
    category: "Graphic Design",
    image: "https://images.pexels.com/photos/196645/pexels-photo-196645.jpeg?auto=compress&cs=tinysrgb&w=600",
    link: "#"
  },
  {
    id: 4,
    title: "Restaurant Website",
    category: "Web Design",
    image: "https://images.pexels.com/photos/461198/pexels-photo-461198.jpeg?auto=compress&cs=tinysrgb&w=600",
    link: "#"
  },
  {
    id: 5,
    title: "Fitness App Interface",
    category: "Mobile Design",
    image: "https://images.pexels.com/photos/196644/pexels-photo-196644.jpeg?auto=compress&cs=tinysrgb&w=600",
    link: "#"
  },
  {
    id: 6,
    title: "Startup Logo Design",
    category: "Logo",
    image: "https://images.pexels.com/photos/265087/pexels-photo-265087.jpeg?auto=compress&cs=tinysrgb&w=600",
    link: "#"
  }
])
</script>

<style scoped>
.pilot-works-section {
  background: #111111;
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

.works-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
  gap: 2rem;
  margin-bottom: 4rem;
}

.work-card {
  background: var(--gradient-card);
  border-radius: 1.5rem;
  overflow: hidden;
  border: 1px solid var(--border-color);
  transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
  backdrop-filter: blur(10px);
}

.work-card:hover {
  transform: translateY(-12px);
  box-shadow: var(--shadow-primary);
  border-color: var(--primary-purple);
}

.work-image {
  position: relative;
  height: 250px;
  overflow: hidden;
}

.work-image img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.4s ease;
}

.work-card:hover .work-image img {
  transform: scale(1.1);
}

.work-overlay {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(0, 0, 0, 0.7);
  display: flex;
  align-items: center;
  justify-content: center;
  opacity: 0;
  transition: opacity 0.3s ease;
}

.work-card:hover .work-overlay {
  opacity: 1;
}

.visit-btn {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  padding: 0.875rem 1.5rem;
  background: var(--gradient-primary);
  color: white;
  text-decoration: none;
  border-radius: 2rem;
  font-weight: 500;
  transition: all 0.3s ease;
  box-shadow: var(--shadow-soft);
}

.visit-btn:hover {
  transform: translateY(-2px);
  box-shadow: var(--shadow-primary);
}

.work-content {
  padding: 1.5rem;
}

.work-title {
  font-size: 1.25rem;
  font-weight: 600;
  color: var(--text-primary);
  margin-bottom: 0.5rem;
}

.work-category {
  color: var(--text-muted);
  font-size: 0.9rem;
  text-transform: uppercase;
  letter-spacing: 0.05em;
}

.section-footer {
  text-align: center;
}

.btn svg {
  margin-left: 0.5rem;
  transition: transform 0.3s ease;
}

.btn:hover svg {
  transform: translateX(4px);
}

@media (max-width: 768px) {
  .works-grid {
    grid-template-columns: 1fr;
    gap: 1.5rem;
  }

  .work-card {
    margin: 0 auto;
    max-width: 400px;
  }

  .work-image {
    height: 200px;
  }

  .section-header {
    margin-bottom: 3rem;
  }
}
</style>
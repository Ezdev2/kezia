<template>
  <div class="works-page">
    <div class="works-header section">
      <div class="container">
        <div class="header-content" data-aos="fade-up">
          <h1 class="page-title">My Works</h1>
          <p class="page-subtitle">A comprehensive collection of my design projects</p>
        </div>

        <!-- Category Filter -->
        <div class="filter-tabs" data-aos="fade-up" data-aos-delay="200">
          <button 
            v-for="category in categories"
            :key="category.id"
            class="filter-button"
            :class="{ active: activeCategory === category.id }"
            @click="setActiveCategory(category.id)"
          >
            <div v-html="category.icon"></div>
            {{ category.name }}
          </button>
        </div>
      </div>
    </div>

    <div class="works-content section">
      <div class="container">
        <transition-group name="works-list" tag="div" class="works-grid">
          <div 
            v-for="work in filteredWorks" 
            :key="work.id"
            class="work-item"
          >
            <div class="work-card">
              <div class="work-image">
                <img :src="work.image" :alt="work.title" />
                <div class="work-overlay">
                  <div class="overlay-content">
                    <a :href="work.link" target="_blank" class="visit-btn">
                      <svg width="24" height="24" viewBox="0 0 24 24" fill="none">
                        <path d="M7 17L17 7M17 7H7M17 7V17" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                      </svg>
                      Visit Project
                    </a>
                    <p class="work-preview">{{ work.description }}</p>
                  </div>
                </div>
              </div>
              <div class="work-content">
                <div class="work-header">
                  <h3 class="work-title">{{ work.title }}</h3>
                  <span class="work-category">{{ work.category }}</span>
                </div>
                <div class="work-tags">
                  <span v-for="tag in work.tags" :key="tag" class="work-tag">
                    {{ tag }}
                  </span>
                </div>
              </div>
            </div>
          </div>
        </transition-group>

        <!-- Empty State -->
        <div v-if="filteredWorks.length === 0" class="empty-state" data-aos="fade-up">
          <svg width="64" height="64" viewBox="0 0 24 24" fill="none">
            <circle cx="12" cy="12" r="10" stroke="currentColor" stroke-width="2"/>
            <path d="M16 16s-1.5-2-4-2-4 2-4 2" stroke="currentColor" stroke-width="2"/>
            <line x1="9" y1="9" x2="9.01" y2="9" stroke="currentColor" stroke-width="2"/>
            <line x1="15" y1="9" x2="15.01" y2="9" stroke="currentColor" stroke-width="2"/>
          </svg>
          <h3>No projects found</h3>
          <p>Try selecting a different category to see more projects.</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, computed } from 'vue'

interface WorkItem {
  id: number
  title: string
  category: string
  image: string
  link: string
  description: string
  tags: string[]
}

interface Category {
  id: string
  name: string
  icon: string
}

const activeCategory = ref('all')

const categories = ref<Category[]>([
  {
    id: 'all',
    name: 'All Projects',
    icon: `<svg width="20" height="20" viewBox="0 0 24 24" fill="none">
      <rect x="3" y="3" width="7" height="7" stroke="currentColor" stroke-width="2"/>
      <rect x="14" y="3" width="7" height="7" stroke="currentColor" stroke-width="2"/>
      <rect x="14" y="14" width="7" height="7" stroke="currentColor" stroke-width="2"/>
      <rect x="3" y="14" width="7" height="7" stroke="currentColor" stroke-width="2"/>
    </svg>`
  },
  {
    id: 'web',
    name: 'Web Design',
    icon: `<svg width="20" height="20" viewBox="0 0 24 24" fill="none">
      <rect x="2" y="3" width="20" height="14" rx="2" ry="2" stroke="currentColor" stroke-width="2"/>
      <line x1="8" y1="21" x2="16" y2="21" stroke="currentColor" stroke-width="2"/>
      <line x1="12" y1="17" x2="12" y2="21" stroke="currentColor" stroke-width="2"/>
    </svg>`
  },
  {
    id: 'mobile',
    name: 'Mobile Design',
    icon: `<svg width="20" height="20" viewBox="0 0 24 24" fill="none">
      <rect x="5" y="2" width="14" height="20" rx="2" ry="2" stroke="currentColor" stroke-width="2"/>
      <line x1="12" y1="18" x2="12.01" y2="18" stroke="currentColor" stroke-width="2"/>
    </svg>`
  },
  {
    id: 'graphic',
    name: 'Graphic Design',
    icon: `<svg width="20" height="20" viewBox="0 0 24 24" fill="none">
      <path d="M12 19l7-7 3 3-7 7-3-3z" stroke="currentColor" stroke-width="2"/>
      <path d="m18 13-1.5-7.5L2 2l3.5 14.5L13 18l5-5z" stroke="currentColor" stroke-width="2"/>
      <path d="m2 2 7.586 7.586" stroke="currentColor" stroke-width="2"/>
      <circle cx="11" cy="11" r="2" stroke="currentColor" stroke-width="2"/>
    </svg>`
  },
  {
    id: 'logo',
    name: 'Logo Design',
    icon: `<svg width="20" height="20" viewBox="0 0 24 24" fill="none">
      <polygon points="13,2 3,14 12,14 11,22 21,10 12,10 13,2" stroke="currentColor" stroke-width="2"/>
    </svg>`
  }
])

const allWorks = ref<WorkItem[]>([
  {
    id: 1,
    title: "E-commerce Mobile App",
    category: "mobile",
    image: "https://images.pexels.com/photos/196644/pexels-photo-196644.jpeg?auto=compress&cs=tinysrgb&w=600",
    link: "#",
    description: "A modern mobile app for seamless shopping experience with intuitive navigation and secure checkout.",
    tags: ["React Native", "UI/UX", "Mobile"]
  },
  {
    id: 2,
    title: "Financial Dashboard",
    category: "web",
    image: "https://images.pexels.com/photos/265087/pexels-photo-265087.jpeg?auto=compress&cs=tinysrgb&w=600",
    link: "#",
    description: "Comprehensive financial dashboard with real-time data visualization and analytics.",
    tags: ["Dashboard", "Data Viz", "Web App"]
  },
  {
    id: 3,
    title: "Brand Identity Design",
    category: "graphic",
    image: "https://images.pexels.com/photos/196645/pexels-photo-196645.jpeg?auto=compress&cs=tinysrgb&w=600",
    link: "#",
    description: "Complete brand identity package including logo, color palette, and brand guidelines.",
    tags: ["Branding", "Identity", "Print"]
  },
  {
    id: 4,
    title: "Restaurant Website",
    category: "web",
    image: "https://images.pexels.com/photos/461198/pexels-photo-461198.jpeg?auto=compress&cs=tinysrgb&w=600",
    link: "#",
    description: "Elegant restaurant website with online reservations and menu showcase.",
    tags: ["Restaurant", "Booking", "Web"]
  },
  {
    id: 5,
    title: "Fitness App Interface",
    category: "mobile",
    image: "https://images.pexels.com/photos/841130/pexels-photo-841130.jpeg?auto=compress&cs=tinysrgb&w=600",
    link: "#",
    description: "Motivating fitness app with workout tracking and progress visualization.",
    tags: ["Fitness", "Tracking", "Mobile"]
  },
  {
    id: 6,
    title: "Startup Logo Design",
    category: "logo",
    image: "https://images.pexels.com/photos/533189/pexels-photo-533189.jpeg?auto=compress&cs=tinysrgb&w=600",
    link: "#",
    description: "Modern and memorable logo design for a tech startup with scalable variations.",
    tags: ["Logo", "Startup", "Tech"]
  },
  {
    id: 7,
    title: "Travel Blog Website",
    category: "web",
    image: "https://images.pexels.com/photos/1591447/pexels-photo-1591447.jpeg?auto=compress&cs=tinysrgb&w=600",
    link: "#",
    description: "Beautiful travel blog with immersive storytelling and photo galleries.",
    tags: ["Blog", "Travel", "Photography"]
  },
  {
    id: 8,
    title: "Banking App Design",
    category: "mobile",
    image: "https://images.pexels.com/photos/259200/pexels-photo-259200.jpeg?auto=compress&cs=tinysrgb&w=600",
    link: "#",
    description: "Secure and user-friendly banking app with intuitive transaction management.",
    tags: ["Banking", "Security", "Fintech"]
  },
  {
    id: 9,
    title: "Magazine Layout",
    category: "graphic",
    image: "https://images.pexels.com/photos/1288572/pexels-photo-1288572.jpeg?auto=compress&cs=tinysrgb&w=600",
    link: "#",
    description: "Editorial design for fashion magazine with dynamic layouts and typography.",
    tags: ["Editorial", "Magazine", "Typography"]
  },
  {
    id: 10,
    title: "Coffee Brand Logo",
    category: "logo",
    image: "https://images.pexels.com/photos/302899/pexels-photo-302899.jpeg?auto=compress&cs=tinysrgb&w=600",
    link: "#",
    description: "Artisan coffee brand logo with hand-crafted aesthetic and versatile applications.",
    tags: ["Coffee", "Artisan", "Brand"]
  },
  {
    id: 11,
    title: "Real Estate Platform",
    category: "web",
    image: "https://images.pexels.com/photos/1370704/pexels-photo-1370704.jpeg?auto=compress&cs=tinysrgb&w=600",
    link: "#",
    description: "Comprehensive real estate platform with advanced search and virtual tours.",
    tags: ["Real Estate", "Search", "Platform"]
  },
  {
    id: 12,
    title: "Health Tracking App",
    category: "mobile",
    image: "https://images.pexels.com/photos/40568/medical-appointment-doctor-healthcare-40568.jpeg?auto=compress&cs=tinysrgb&w=600",
    link: "#",
    description: "Personal health tracking app with symptom monitoring and medical records.",
    tags: ["Health", "Tracking", "Medical"]
  }
])

const filteredWorks = computed(() => {
  if (activeCategory.value === 'all') {
    return allWorks.value
  }
  return allWorks.value.filter(work => work.category === activeCategory.value)
})

const setActiveCategory = (categoryId: string) => {
  activeCategory.value = categoryId
}
</script>

<style scoped>
.works-page {
  padding-top: 6rem;
  min-height: 100vh;
  background: var(--primary-bg);
}

.works-header {
  background: var(--secondary-bg);
  padding: 4rem 0;
}

.header-content {
  text-align: center;
  margin-bottom: 3rem;
}

.page-title {
  font-size: clamp(3rem, 6vw, 4.5rem);
  font-weight: 700;
  color: var(--text-primary);
  margin-bottom: 1rem;
}

.page-subtitle {
  font-size: 1.3rem;
  color: var(--text-muted);
  max-width: 600px;
  margin: 0 auto;
}

.filter-tabs {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 1rem;
}

.filter-button {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  padding: 0.875rem 1.5rem;
  background: transparent;
  border: 2px solid var(--border-color);
  border-radius: 2rem;
  color: var(--text-secondary);
  font-weight: 500;
  font-size: 0.95rem;
  cursor: pointer;
  transition: all 0.3s ease;
}

.filter-button:hover {
  border-color: var(--primary-purple);
  color: var(--text-primary);
}

.filter-button.active {
  background: var(--gradient-primary);
  border-color: transparent;
  color: white;
  box-shadow: var(--shadow-soft);
}

.works-content {
  padding: 4rem 0;
}

.works-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(380px, 1fr));
  gap: 2rem;
}

.work-item {
  opacity: 1;
  transition: all 0.4s ease;
}

.work-card {
  background: var(--gradient-card);
  border-radius: 1.5rem;
  overflow: hidden;
  border: 1px solid var(--border-color);
  transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
  backdrop-filter: blur(10px);
  height: 100%;
  display: flex;
  flex-direction: column;
}

.work-card:hover {
  transform: translateY(-12px);
  box-shadow: var(--shadow-primary);
  border-color: var(--primary-purple);
}

.work-image {
  position: relative;
  height: 280px;
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
  background: rgba(0, 0, 0, 0.85);
  display: flex;
  align-items: center;
  justify-content: center;
  opacity: 0;
  transition: opacity 0.3s ease;
}

.work-card:hover .work-overlay {
  opacity: 1;
}

.overlay-content {
  text-align: center;
  padding: 2rem;
}

.visit-btn {
  display: inline-flex;
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
  margin-bottom: 1rem;
}

.visit-btn:hover {
  transform: translateY(-2px);
  box-shadow: var(--shadow-primary);
}

.work-preview {
  color: var(--text-secondary);
  font-size: 0.9rem;
  line-height: 1.5;
}

.work-content {
  padding: 2rem;
  flex: 1;
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.work-header {
  margin-bottom: 1rem;
}

.work-title {
  font-size: 1.4rem;
  font-weight: 600;
  color: var(--text-primary);
  margin-bottom: 0.5rem;
}

.work-category {
  color: var(--secondary-purple);
  font-size: 0.9rem;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  font-weight: 500;
}

.work-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
  margin-top: auto;
}

.work-tag {
  padding: 0.25rem 0.75rem;
  background: rgba(168, 85, 247, 0.1);
  color: var(--primary-purple);
  border: 1px solid rgba(168, 85, 247, 0.2);
  border-radius: 1rem;
  font-size: 0.8rem;
  font-weight: 500;
}

.empty-state {
  text-align: center;
  padding: 4rem 2rem;
  color: var(--text-muted);
  grid-column: 1 / -1;
}

.empty-state svg {
  margin-bottom: 2rem;
  color: var(--text-muted);
}

.empty-state h3 {
  font-size: 1.5rem;
  color: var(--text-secondary);
  margin-bottom: 0.5rem;
}

/* Transition animations */
.works-list-enter-active {
  transition: all 0.5s ease;
}

.works-list-leave-active {
  transition: all 0.3s ease;
}

.works-list-enter-from {
  opacity: 0;
  transform: translateY(30px) scale(0.95);
}

.works-list-leave-to {
  opacity: 0;
  transform: translateY(-30px) scale(0.95);
}

.works-list-move {
  transition: transform 0.4s ease;
}

@media (max-width: 1024px) {
  .works-grid {
    grid-template-columns: repeat(auto-fill, minmax(320px, 1fr));
    gap: 1.5rem;
  }
}

@media (max-width: 768px) {
  .works-page {
    padding-top: 5rem;
  }

  .works-header {
    padding: 3rem 0;
  }

  .works-grid {
    grid-template-columns: 1fr;
    gap: 1.5rem;
  }

  .filter-tabs {
    flex-direction: column;
    align-items: center;
    gap: 0.75rem;
  }

  .filter-button {
    width: 100%;
    max-width: 300px;
    justify-content: center;
  }

  .work-image {
    height: 220px;
  }

  .work-content {
    padding: 1.5rem;
  }
}
</style>
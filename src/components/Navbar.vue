<template>
  <nav class="navbar" :class="{ 'navbar-scrolled': isScrolled }" ref="navbar">
    <div class="container">
      <div class="navbar-content">
        <!-- Logo -->
        <a href="/" class="navbar-brand" data-aos="fade-right">
          <h3 class="brand-text">Kezia</h3>
        </a>

        <!-- Navigation Links -->
        <div class="navbar-nav" :class="{ 'navbar-nav-open': mobileMenuOpen }">
          <router-link  
            to="/#hero" 
            class="nav-link"
            :class="{ active: $route.name === 'Home' && activeSection === 'hero' }"
            @click="scrollToSection('hero')"
          >
            Home
          </router-link>
          <router-link 
            to="/works" 
            class="nav-link"
            :class="{ active: $route.name === 'Works' }"
          >
            My Works
          </router-link>
          <router-link  
            to="/#cv" 
            class="nav-link"
            :class="{ active: activeSection === 'cv' }"
            @click="scrollToSection('cv')"
          >
            CV
          </router-link>
          <router-link  
            to="/#contact" 
            class="nav-link"
            :class="{ active: activeSection === 'contact' }"
            @click="scrollToSection('contact')"
          >
            Contact Me
          </router-link>
        </div>

        <!-- Mobile Menu Toggle -->
        <button 
          class="mobile-toggle"
          @click="toggleMobileMenu"
          :class="{ active: mobileMenuOpen }"
        >
          <span></span>
          <span></span>
          <span></span>
        </button>
      </div>
    </div>
  </nav>
</template>

<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue'
import { useRoute } from 'vue-router'

const route = useRoute()
const isScrolled = ref(false)
const activeSection = ref('hero')
const mobileMenuOpen = ref(false)
const navbar = ref<HTMLElement>()

const handleScroll = () => {
  isScrolled.value = window.scrollY > 50
  
  // Update active section based on scroll position
  if (route.name === 'Home') {
    const sections = ['hero', 'works', 'why-me', 'cv', 'contact']
    
    for (const section of sections) {
      const element = document.getElementById(section)
      if (element) {
        const rect = element.getBoundingClientRect()
        if (rect.top <= 100 && rect.bottom >= 100) {
          activeSection.value = section
          break
        }
      }
    }
  }
}

const scrollToSection = (sectionId: string) => {
  const element = document.getElementById(sectionId)
  if (element) {
    const offsetTop = element.offsetTop - 80
    window.scrollTo({
      top: offsetTop,
      behavior: 'smooth'
    })
  }
  mobileMenuOpen.value = false
}

const toggleMobileMenu = () => {
  mobileMenuOpen.value = !mobileMenuOpen.value
}

onMounted(() => {
  window.addEventListener('scroll', handleScroll)
  handleScroll()
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
})
</script>

<style scoped>
.navbar {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 1000;
  padding: 1rem 0;
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
  background: rgba(26, 26, 46, 0.1);
  backdrop-filter: blur(10px);
}

.navbar-scrolled {
  background: rgba(26, 26, 46, 0.95);
  padding: 0.5rem 0;
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.3);
}

.navbar-content {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.brand-text {
  background: var(--gradient-primary);
  background-clip: text;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  font-weight: 700;
  font-size: 1.5rem;
}

.navbar-nav {
  display: flex;
  align-items: center;
  gap: 2rem;
}

.nav-link {
  color: var(--text-secondary);
  text-decoration: none;
  font-weight: 500;
  font-size: 0.95rem;
  transition: all 0.3s ease;
  position: relative;
  padding: 0.5rem 0;
}

.nav-link::after {
  content: '';
  position: absolute;
  bottom: 0;
  left: 0;
  width: 0;
  height: 2px;
  background: var(--gradient-primary);
  transition: width 0.3s ease;
}

.nav-link:hover,
.nav-link.active {
  color: var(--text-primary);
}

.nav-link:hover::after,
.nav-link.active::after {
  width: 100%;
}

.mobile-toggle {
  display: none;
  flex-direction: column;
  justify-content: center;
  width: 30px;
  height: 30px;
  background: none;
  border: none;
  cursor: pointer;
  padding: 0;
}

.mobile-toggle span {
  display: block;
  height: 2px;
  width: 100%;
  background: var(--text-primary);
  margin: 3px 0;
  transition: all 0.3s ease;
  transform-origin: center;
}

.mobile-toggle.active span:nth-child(1) {
  transform: rotate(45deg) translate(5px, 5px);
}

.mobile-toggle.active span:nth-child(2) {
  opacity: 0;
}

.mobile-toggle.active span:nth-child(3) {
  transform: rotate(-45deg) translate(7px, -6px);
}
.navbar-brand {
  text-decoration: none;
}

@media (max-width: 768px) {
  .mobile-toggle {
    display: flex;
  }

  .navbar-nav {
    position: fixed;
    top: 100%;
    left: 0;
    right: 0;
    background: rgba(26, 26, 46, 0.98);
    backdrop-filter: blur(20px);
    flex-direction: column;
    padding: 2rem;
    gap: 1.5rem;
    transform: translateY(-100%);
    opacity: 0;
    visibility: hidden;
    transition: all 0.3s ease;
  }

  .navbar-nav-open {
    transform: translateY(0);
    opacity: 1;
    visibility: visible;
  }

  .nav-link {
    font-size: 1.1rem;
    text-align: center;
    padding: 1rem 0;
  }
}
</style>
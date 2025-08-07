<template>
  <footer class="footer-section">
    <div class="container">
      <div class="footer-content">
        <div class="footer-brand" data-aos="fade-up">
          <h3 class="brand-text">Kezia</h3>
          <p class="brand-tagline">Creating beautiful digital experiences</p>
        </div>

        <div class="footer-links" data-aos="fade-up" data-aos-delay="200">
          <div class="link-group">
            <h4 class="link-title">Navigation</h4>
            <div class="link-list">
              <router-link to="/" class="footer-link">Home</router-link>
              <router-link to="/works" class="footer-link">My Works</router-link>
              <a href="#cv" @click="scrollToSection('cv')" class="footer-link">CV</a>
              <a href="#contact" @click="scrollToSection('contact')" class="footer-link">Contact</a>
            </div>
          </div>

          <div class="link-group">
            <h4 class="link-title">Services</h4>
            <div class="link-list">
              <span class="footer-link">UI/UX Design</span>
              <span class="footer-link">Web Design</span>
              <span class="footer-link">Mobile Design</span>
              <span class="footer-link">Brand Design</span>
            </div>
          </div>

          <div class="link-group">
            <h4 class="link-title">Connect</h4>
            <div class="social-links">
              <a href="#" class="social-link" target="_blank">
                <svg width="20" height="20" viewBox="0 0 24 24" fill="currentColor">
                  <path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433c-1.144 0-2.063-.926-2.063-2.065 0-1.138.92-2.063 2.063-2.063 1.14 0 2.064.925 2.064 2.063 0 1.139-.925 2.065-2.064 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/>
                </svg>
                LinkedIn
              </a>
              <a href="#" class="social-link" target="_blank">
                <svg width="20" height="20" viewBox="0 0 24 24" fill="currentColor">
                  <path d="M12 2.163c3.204 0 3.584.012 4.85.07 3.252.148 4.771 1.691 4.919 4.919.058 1.265.069 1.645.069 4.849 0 3.205-.012 3.584-.069 4.849-.149 3.225-1.664 4.771-4.919 4.919-1.266.058-1.644.07-4.85.07-3.204 0-3.584-.012-4.849-.07-3.26-.149-4.771-1.699-4.919-4.92-.058-1.265-.07-1.644-.07-4.849 0-3.204.013-3.583.07-4.849.149-3.227 1.664-4.771 4.919-4.919 1.266-.057 1.645-.069 4.849-.069zm0-2.163c-3.259 0-3.667.014-4.947.072-4.358.2-6.78 2.618-6.98 6.98-.059 1.281-.073 1.689-.073 4.948 0 3.259.014 3.668.072 4.948.2 4.358 2.618 6.78 6.98 6.98 1.281.058 1.689.072 4.948.072 3.259 0 3.668-.014 4.948-.072 4.354-.2 6.782-2.618 6.979-6.98.059-1.28.073-1.689.073-4.948 0-3.259-.014-3.667-.072-4.947-.196-4.354-2.617-6.78-6.979-6.98-1.281-.059-1.69-.073-4.949-.073zm0 5.838c-3.403 0-6.162 2.759-6.162 6.162s2.759 6.163 6.162 6.163 6.162-2.759 6.162-6.163c0-3.403-2.759-6.162-6.162-6.162zm0 10.162c-2.209 0-4-1.79-4-4 0-2.209 1.791-4 4-4s4 1.791 4 4c0 2.21-1.791 4-4 4zm6.406-11.845c-.796 0-1.441.645-1.441 1.44s.645 1.44 1.441 1.44c.795 0 1.439-.645 1.439-1.44s-.644-1.44-1.439-1.44z"/>
                </svg>
                Instagram
              </a>
              <a href="#" class="social-link" target="_blank">
                <svg width="20" height="20" viewBox="0 0 24 24" fill="currentColor">
                  <path d="M24 4.557c-.883.392-1.832.656-2.828.775 1.017-.609 1.798-1.574 2.165-2.724-.951.564-2.005.974-3.127 1.195-.897-.957-2.178-1.555-3.594-1.555-3.179 0-5.515 2.966-4.797 6.045-4.091-.205-7.719-2.165-10.148-5.144-1.29 2.213-.669 5.108 1.523 6.574-.806-.026-1.566-.247-2.229-.616-.054 2.281 1.581 4.415 3.949 4.89-.693.188-1.452.232-2.224.084.626 1.956 2.444 3.379 4.6 3.419-2.07 1.623-4.678 2.348-7.29 2.04 2.179 1.397 4.768 2.212 7.548 2.212 9.142 0 14.307-7.721 13.995-14.646.962-.695 1.797-1.562 2.457-2.549z"/>
                </svg>
                Twitter
              </a>
            </div>
          </div>
        </div>
      </div>

      <div class="footer-bottom" data-aos="fade-up" data-aos-delay="400">
        <div class="footer-copyright">
          <p>&copy; {{ new Date().getFullYear() }} Kezia. All rights reserved.</p>
        </div>
        <button class="scroll-to-top" @click="scrollToTop">
          <svg width="20" height="20" viewBox="0 0 24 24" fill="none">
            <path d="M18 15L12 9L6 15" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
          </svg>
          Back to Top
        </button>
      </div>
    </div>
  </footer>
</template>

<script setup lang="ts">
const scrollToSection = (sectionId: string) => {
  const element = document.getElementById(sectionId)
  if (element) {
    const offsetTop = element.offsetTop - 80
    window.scrollTo({
      top: offsetTop,
      behavior: 'smooth'
    })
  }
}

const scrollToTop = () => {
  window.scrollTo({
    top: 0,
    behavior: 'smooth'
  })
}
</script>

<style scoped>
.footer-section {
  background: var(--accent-bg);
  padding: 4rem 0 2rem;
  border-top: 1px solid var(--border-color);
}

.footer-content {
  display: grid;
  grid-template-columns: 1fr 2fr;
  gap: 4rem;
  margin-bottom: 3rem;
}

.footer-brand {
  max-width: 300px;
}

.brand-text {
  background: var(--gradient-primary);
  background-clip: text;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  font-weight: 700;
  font-size: 2rem;
  margin-bottom: 1rem;
}

.brand-tagline {
  color: var(--text-secondary);
  font-size: 1.1rem;
  line-height: 1.6;
}

.footer-links {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 3rem;
}

.link-title {
  font-size: 1.1rem;
  font-weight: 600;
  color: var(--text-primary);
  margin-bottom: 1rem;
}

.link-list {
  display: flex;
  flex-direction: column;
  gap: 0.75rem;
}

.footer-link {
  color: var(--text-secondary);
  text-decoration: none;
  font-size: 0.95rem;
  transition: all 0.3s ease;
  cursor: pointer;
}

.footer-link:hover {
  color: var(--primary-purple);
  transform: translateX(4px);
}

.social-links {
  display: flex;
  flex-direction: column;
  gap: 0.75rem;
}

.social-link {
  display: flex;
  align-items: center;
  gap: 0.75rem;
  color: var(--text-secondary);
  text-decoration: none;
  font-size: 0.95rem;
  transition: all 0.3s ease;
}

.social-link:hover {
  color: var(--primary-purple);
  transform: translateX(4px);
}

.footer-bottom {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding-top: 2rem;
  border-top: 1px solid var(--border-color);
}

.footer-copyright p {
  color: var(--text-muted);
  font-size: 0.9rem;
}

.scroll-to-top {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  padding: 0.75rem 1.5rem;
  background: transparent;
  border: 1px solid var(--border-color);
  border-radius: 2rem;
  color: var(--text-secondary);
  font-size: 0.9rem;
  font-weight: 500;
  cursor: pointer;
  transition: all 0.3s ease;
}

.scroll-to-top:hover {
  background: var(--gradient-primary);
  color: white;
  border-color: transparent;
  transform: translateY(-2px);
}

.scroll-to-top svg {
  transition: transform 0.3s ease;
}

.scroll-to-top:hover svg {
  transform: translateY(-2px);
}

@media (max-width: 1024px) {
  .footer-content {
    grid-template-columns: 1fr;
    gap: 3rem;
  }

  .footer-links {
    grid-template-columns: repeat(2, 1fr);
    gap: 2rem;
  }
}

@media (max-width: 768px) {
  .footer-section {
    padding: 3rem 0 1.5rem;
  }

  .footer-links {
    grid-template-columns: 1fr;
    gap: 2rem;
  }

  .footer-bottom {
    flex-direction: column;
    gap: 1.5rem;
    text-align: center;
  }
}
</style>
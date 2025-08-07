<template>
  <section id="hero">
    <div class="hero-grid">
      <!-- Left Column -->
      <div class="hero-text">
        <h1>
          Hey, I'm <span class="text-gradient">Kezia</span>, a web and mobile designer with
          <span class="text-gradient">5+ years</span> of experience.
        </h1>
        <p>
          I create beautiful, user-centered digital experiences that blend creativity with functionality. From elegant
          web interfaces to intuitive mobile apps, I bring ideas to life with passion and precision.
        </p>

        <div class="social-links" data-aos="fade-up" data-aos-delay="600">
          <a href="#" class="social-link" target="_blank">
            <svg width="20" height="20" viewBox="0 0 24 24" fill="currentColor">
              <path
                d="M24 4.557c-.883.392-1.832.656-2.828.775 1.017-.609 1.798-1.574 2.165-2.724-.951.564-2.005.974-3.127 1.195-.897-.957-2.178-1.555-3.594-1.555-3.179 0-5.515 2.966-4.797 6.045-4.091-.205-7.719-2.165-10.148-5.144-1.29 2.213-.669 5.108 1.523 6.574-.806-.026-1.566-.247-2.229-.616-.054 2.281 1.581 4.415 3.949 4.89-.693.188-1.452.232-2.224.084.626 1.956 2.444 3.379 4.6 3.419-2.07 1.623-4.678 2.348-7.29 2.04 2.179 1.397 4.768 2.212 7.548 2.212 9.142 0 14.307-7.721 13.995-14.646.962-.695 1.797-1.562 2.457-2.549z" />
            </svg>
          </a>
          <a href="#" class="social-link" target="_blank">
            <svg width="20" height="20" viewBox="0 0 24 24" fill="currentColor">
              <path
                d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433c-1.144 0-2.063-.926-2.063-2.065 0-1.138.92-2.063 2.063-2.063 1.14 0 2.064.925 2.064 2.063 0 1.139-.925 2.065-2.064 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z" />
            </svg>
          </a>
          <a href="#" class="social-link" target="_blank">
            <svg width="20" height="20" viewBox="0 0 24 24" fill="currentColor">
              <path
                d="M12 2.163c3.204 0 3.584.012 4.85.07 3.252.148 4.771 1.691 4.919 4.919.058 1.265.069 1.645.069 4.849 0 3.205-.012 3.584-.069 4.849-.149 3.225-1.664 4.771-4.919 4.919-1.266.058-1.644.07-4.85.07-3.204 0-3.584-.012-4.849-.07-3.26-.149-4.771-1.699-4.919-4.92-.058-1.265-.07-1.644-.07-4.849 0-3.204.013-3.583.07-4.849.149-3.227 1.664-4.771 4.919-4.919 1.266-.057 1.645-.069 4.849-.069zm0-2.163c-3.259 0-3.667.014-4.947.072-4.358.2-6.78 2.618-6.98 6.98-.059 1.281-.073 1.689-.073 4.948 0 3.259.014 3.668.072 4.948.2 4.358 2.618 6.78 6.98 6.98 1.281.058 1.689.072 4.948.072 3.259 0 3.668-.014 4.948-.072 4.354-.2 6.782-2.618 6.979-6.98.059-1.28.073-1.689.073-4.948 0-3.259-.014-3.667-.072-4.947-.196-4.354-2.617-6.78-6.979-6.98-1.281-.059-1.69-.073-4.949-.073zm0 5.838c-3.403 0-6.162 2.759-6.162 6.162s2.759 6.163 6.162 6.163 6.162-2.759 6.162-6.163c0-3.403-2.759-6.162-6.162-6.162zm0 10.162c-2.209 0-4-1.79-4-4 0-2.209 1.791-4 4-4s4 1.791 4 4c0 2.21-1.791 4-4 4zm6.406-11.845c-.796 0-1.441.645-1.441 1.44s.645 1.44 1.441 1.44c.795 0 1.439-.645 1.439-1.44s-.644-1.44-1.439-1.44z" />
            </svg>
          </a>
        </div>
      </div>

      <!-- Right Column -->
      <div class="hero-image">
        <img src="https://images.pexels.com/photos/31708892/pexels-photo-31708892.jpeg?auto=compress&cs=tinysrgb&w=800"
          alt="Kezia - Senior Designer"/>
      </div>
    </div>
  </section>

</template>

<script setup lang="ts">
const scrollToContact = () => {
  const element = document.getElementById('contact')
  if (element) {
    const offsetTop = element.offsetTop - 80
    window.scrollTo({
      top: offsetTop,
      behavior: 'smooth'
    })
  }
}

const scrollToWorks = () => {
  const element = document.getElementById('works')
  if (element) {
    const offsetTop = element.offsetTop - 80
    window.scrollTo({
      top: offsetTop,
      behavior: 'smooth'
    })
  }
}
</script>

<style scoped>

/* new */
#hero {
  padding: 4rem 0;
}

.hero-grid {
  display: grid;
  grid-template-columns: 2fr 1fr;
  gap: 3rem;
  align-items: center;
  max-width: 1200px;
  margin: 80px auto;
}

@media (max-width: 1024px) {
  .hero-grid {
    grid-template-columns: 1fr;
  }
}

/* Text block */
.hero-text {
  background: rgba(255, 255, 255, 0.068);
  backdrop-filter: blur(20px);
  padding: 2rem;
  border-radius: 1.5rem;
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.1);
  height: -webkit-fill-available;
  display: flex;
  flex-direction: column;
  justify-content: center;
}

.hero-text h1 {
  font-size: 2.5rem;
  font-weight: bold;
  line-height: 1.3;
  margin-bottom: 1.5rem;
}

.hero-text p {
  font-size: 1.125rem;
  color: #4b5563;
  margin-bottom: 2rem;
}

.text-gradient {
  background: linear-gradient(to right, #7f5af0, #ff80b5);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}

/* Social links */
.social-links {
  display: flex;
  gap: 1rem;
  z-index: 10;
}

.social-link {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 48px;
  height: 48px;
  background: var(--gradient-card);
  border: 1px solid var(--border-color);
  border-radius: 50%;
  color: var(--text-secondary);
  text-decoration: none;
  transition: all 0.3s ease;
  backdrop-filter: blur(10px);
}

.social-link:hover {
  background: var(--gradient-primary);
  color: white;
  transform: translateY(-2px);
  box-shadow: var(--shadow-soft);
}

@media (max-width: 1024px) {
  .social-links {
    position: static;
    flex-direction: row;
    justify-content: center;
    transform: none;
    margin-top: 3rem;
  }
}

/* Button */
#contactBtn {
  background-color: #111827;
  color: white;
  font-weight: 600;
  padding: 0.75rem 2rem;
  border: none;
  border-radius: 0.5rem;
  cursor: pointer;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);
  transition: background-color 0.3s;
}

#contactBtn:hover {
  background-color: #1f2937;
}

/* Image */
.hero-image {
  display: flex;
  justify-content: center;
  align-items: center;
}

.hero-image img {
  max-width: 100%;
  height: auto;
  border-radius: 1.5rem;
  object-fit: cover;
  box-shadow: 0 10px 40px rgba(0, 0, 0, 0.2);
}
</style>
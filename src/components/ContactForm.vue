<template>
  <section id="contact" class="contact-section section">
    <div class="container">
      <div class="section-header" data-aos="fade-up">
        <h2 class="section-title">Let's Work Together</h2>
        <p class="section-subtitle">Ready to bring your vision to life? Drop me a message!</p>
      </div>

      <div class="contact-content">
        <div class="contact-form-container" data-aos="fade-right" data-aos-delay="200">
          <form 
            class="contact-form"
            action="https://usebasin.com/f/your-form-endpoint"
            method="POST"
            @submit="handleSubmit"
            ref="contactForm"
          >
            <div class="form-group">
              <label for="name" class="form-label">Name</label>
              <input
                type="text"
                id="name"
                name="name"
                v-model="formData.name"
                class="form-input"
                :class="{ error: errors.name }"
                placeholder="Your full name"
                required
              />
              <span v-if="errors.name" class="error-message">{{ errors.name }}</span>
            </div>

            <div class="form-group">
              <label for="email" class="form-label">Email</label>
              <input
                type="email"
                id="email"
                name="email"
                v-model="formData.email"
                class="form-input"
                :class="{ error: errors.email }"
                placeholder="your.email@example.com"
                required
              />
              <span v-if="errors.email" class="error-message">{{ errors.email }}</span>
            </div>

            <div class="form-group">
              <label for="message" class="form-label">Message</label>
              <textarea
                id="message"
                name="message"
                v-model="formData.message"
                class="form-textarea"
                :class="{ error: errors.message }"
                placeholder="Tell me about your project..."
                rows="6"
                required
              ></textarea>
              <span v-if="errors.message" class="error-message">{{ errors.message }}</span>
            </div>

            <button 
              type="submit" 
              class="btn btn-primary submit-btn"
              :disabled="isSubmitting"
              :class="{ loading: isSubmitting }"
            >
              <span v-if="!isSubmitting" class="btn-text">
                Send Message
                <svg width="20" height="20" viewBox="0 0 24 24" fill="none">
                  <path d="M22 2L11 13" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                  <polygon points="22,2 15,22 11,13 2,9 22,2" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                </svg>
              </span>
              <span v-else class="btn-text">
                <div class="loading-spinner"></div>
                Sending...
              </span>
            </button>
          </form>

          <!-- Success/Error Messages -->
          <transition name="fade">
            <div v-if="submitStatus === 'success'" class="status-message success">
              <svg width="24" height="24" viewBox="0 0 24 24" fill="none">
                <path d="M20 6L9 17L4 12" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
              </svg>
              Thank you! Your message has been sent successfully.
            </div>
            <div v-else-if="submitStatus === 'error'" class="status-message error">
              <svg width="24" height="24" viewBox="0 0 24 24" fill="none">
                <circle cx="12" cy="12" r="10" stroke="currentColor" stroke-width="2"/>
                <line x1="15" y1="9" x2="9" y2="15" stroke="currentColor" stroke-width="2"/>
                <line x1="9" y1="9" x2="15" y2="15" stroke="currentColor" stroke-width="2"/>
              </svg>
              Oops! Something went wrong. Please try again.
            </div>
          </transition>
        </div>

        <div class="contact-info" data-aos="fade-left" data-aos-delay="400">
          <div class="info-card">
            <div class="info-icon">
              <svg width="32" height="32" viewBox="0 0 24 24" fill="none">
                <path d="M4 4H20C21.1 4 22 4.9 22 6V18C22 19.1 21.1 20 20 20H4C2.9 20 2 19.1 2 18V6C2 4.9 2.9 4 4 4Z" stroke="currentColor" stroke-width="2"/>
                <polyline points="22,6 12,13 2,6" stroke="currentColor" stroke-width="2"/>
              </svg>
            </div>
            <div class="info-content">
              <h3>Email</h3>
              <p>kezia.designer@email.com</p>
            </div>
          </div>

          <div class="info-card">
            <div class="info-icon">
              <svg width="32" height="32" viewBox="0 0 24 24" fill="none">
                <path d="M21 10C21 17 12 23 12 23S3 17 3 10A9 9 0 0 1 12 1A9 9 0 0 1 21 10Z" stroke="currentColor" stroke-width="2"/>
                <circle cx="12" cy="10" r="3" stroke="currentColor" stroke-width="2"/>
              </svg>
            </div>
            <div class="info-content">
              <h3>Location</h3>
              <p>New York, NY</p>
            </div>
          </div>

          <div class="info-card">
            <div class="info-icon">
              <svg width="32" height="32" viewBox="0 0 24 24" fill="none">
                <circle cx="12" cy="12" r="10" stroke="currentColor" stroke-width="2"/>
                <polyline points="12,6 12,12 16,14" stroke="currentColor" stroke-width="2"/>
              </svg>
            </div>
            <div class="info-content">
              <h3>Response Time</h3>
              <p>Usually within 24 hours</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { ref, reactive } from 'vue'

interface FormData {
  name: string
  email: string
  message: string
}

interface FormErrors {
  name?: string
  email?: string
  message?: string
}

const formData = reactive<FormData>({
  name: '',
  email: '',
  message: ''
})

const errors = reactive<FormErrors>({})
const isSubmitting = ref(false)
const submitStatus = ref<'idle' | 'success' | 'error'>('idle')
const contactForm = ref<HTMLFormElement>()

const validateForm = (): boolean => {
  Object.keys(errors).forEach(key => delete errors[key as keyof FormErrors])

  if (!formData.name.trim()) {
    errors.name = 'Name is required'
  }

  if (!formData.email.trim()) {
    errors.email = 'Email is required'
  } else if (!/\S+@\S+\.\S+/.test(formData.email)) {
    errors.email = 'Please enter a valid email'
  }

  if (!formData.message.trim()) {
    errors.message = 'Message is required'
  } else if (formData.message.trim().length < 10) {
    errors.message = 'Message must be at least 10 characters'
  }

  return Object.keys(errors).length === 0
}

const handleSubmit = async (event: Event) => {
  event.preventDefault()
  
  if (!validateForm()) return

  isSubmitting.value = true
  submitStatus.value = 'idle'

  try {
    // Simulate form submission (replace with actual Basin endpoint)
    await new Promise(resolve => setTimeout(resolve, 2000))
    
    // If using Basin, the form would actually submit via the action attribute
    // For now, we'll simulate success
    submitStatus.value = 'success'
    
    // Reset form
    Object.keys(formData).forEach(key => {
      formData[key as keyof FormData] = ''
    })
    
  } catch (error) {
    submitStatus.value = 'error'
  } finally {
    isSubmitting.value = false
    
    // Clear status after 5 seconds
    setTimeout(() => {
      submitStatus.value = 'idle'
    }, 5000)
  }
}
</script>

<style scoped>
.contact-section {
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

.contact-content {
  display: grid;
  grid-template-columns: 2fr 1fr;
  gap: 4rem;
  align-items: start;
}

.contact-form-container {
  position: relative;
}

.contact-form {
  background: var(--gradient-card);
  border-radius: 1.5rem;
  padding: 3rem;
  border: 1px solid var(--border-color);
  backdrop-filter: blur(10px);
}

.form-group {
  margin-bottom: 2rem;
}

.form-label {
  display: block;
  font-weight: 500;
  color: var(--text-primary);
  margin-bottom: 0.5rem;
  font-size: 0.95rem;
}

.form-input,
.form-textarea {
  width: 100%;
  padding: 1rem 1.25rem;
  background: rgba(255, 255, 255, 0.05);
  border: 1px solid var(--border-color);
  border-radius: 0.75rem;
  color: var(--text-primary);
  font-size: 1rem;
  transition: all 0.3s ease;
  font-family: inherit;
}

.form-input::placeholder,
.form-textarea::placeholder {
  color: var(--text-muted);
}

.form-input:focus,
.form-textarea:focus {
  outline: none;
  border-color: var(--primary-purple);
  box-shadow: 0 0 0 3px rgba(168, 85, 247, 0.1);
}

.form-input.error,
.form-textarea.error {
  border-color: #ef4444;
}

.form-textarea {
  resize: vertical;
  min-height: 120px;
}

.error-message {
  display: block;
  color: #ef4444;
  font-size: 0.85rem;
  margin-top: 0.5rem;
}

.submit-btn {
  width: 100%;
  font-size: 1.1rem;
  padding: 1.25rem;
  position: relative;
  transition: all 0.3s ease;
}

.submit-btn:disabled {
  opacity: 0.7;
  cursor: not-allowed;
}

.btn-text {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 0.5rem;
}

.loading-spinner {
  width: 20px;
  height: 20px;
  border: 2px solid transparent;
  border-top: 2px solid currentColor;
  border-radius: 50%;
  animation: spin 1s linear infinite;
}

@keyframes spin {
  to { transform: rotate(360deg); }
}

.status-message {
  margin-top: 1.5rem;
  padding: 1rem 1.25rem;
  border-radius: 0.75rem;
  display: flex;
  align-items: center;
  gap: 0.75rem;
  font-weight: 500;
}

.status-message.success {
  background: rgba(34, 197, 94, 0.1);
  border: 1px solid rgba(34, 197, 94, 0.3);
  color: #22c55e;
}

.status-message.error {
  background: rgba(239, 68, 68, 0.1);
  border: 1px solid rgba(239, 68, 68, 0.3);
  color: #ef4444;
}

.contact-info {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.info-card {
  background: var(--gradient-card);
  border-radius: 1rem;
  padding: 2rem;
  border: 1px solid var(--border-color);
  backdrop-filter: blur(10px);
  display: flex;
  align-items: center;
  gap: 1rem;
  transition: all 0.3s ease;
}

.info-card:hover {
  transform: translateY(-4px);
  box-shadow: var(--shadow-soft);
  border-color: var(--primary-purple);
}

.info-icon {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 64px;
  height: 64px;
  background: var(--gradient-primary);
  border-radius: 1rem;
  color: white;
  flex-shrink: 0;
}

.info-content h3 {
  font-size: 1.1rem;
  font-weight: 600;
  color: var(--text-primary);
  margin-bottom: 0.25rem;
}

.info-content p {
  color: var(--text-secondary);
  font-size: 0.95rem;
}

.fade-enter-active,
.fade-leave-active {
  transition: all 0.3s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
  transform: translateY(-10px);
}

@media (max-width: 1024px) {
  .contact-content {
    grid-template-columns: 1fr;
    gap: 3rem;
  }
}

@media (max-width: 768px) {
  .contact-form {
    padding: 2rem;
  }

  .info-card {
    flex-direction: column;
    text-align: center;
    padding: 1.5rem;
  }

  .info-icon {
    width: 56px;
    height: 56px;
  }
}
</style>
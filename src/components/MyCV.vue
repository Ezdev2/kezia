<template>
  <section id="cv" class="cv-section section">
    <div class="container">
      <div class="section-header" data-aos="fade-up">
        <h2 class="section-title">My CV</h2>
        <p class="section-subtitle">Professional journey and educational background</p>
      </div>

      <div class="cv-content">
        <!-- Tab Navigation -->
        <div class="cv-tabs" data-aos="fade-up" data-aos-delay="200">
          <button 
            class="tab-button"
            :class="{ active: activeTab === 'experience' }"
            @click="setActiveTab('experience')"
          >
            <svg width="20" height="20" viewBox="0 0 24 24" fill="none">
              <rect x="2" y="3" width="20" height="14" rx="2" ry="2" stroke="currentColor" stroke-width="2"/>
              <line x1="8" y1="21" x2="16" y2="21" stroke="currentColor" stroke-width="2"/>
              <line x1="12" y1="17" x2="12" y2="21" stroke="currentColor" stroke-width="2"/>
            </svg>
            Experience
          </button>
          <button 
            class="tab-button"
            :class="{ active: activeTab === 'education' }"
            @click="setActiveTab('education')"
          >
            <svg width="20" height="20" viewBox="0 0 24 24" fill="none">
              <path d="M22 10V6C22 4.9 21.1 4 20 4H4C2.9 4 2 4.9 2 6V10C3.1 10 4 10.9 4 12S3.1 14 2 14V18C2 19.1 2.9 20 4 20H20C21.1 20 22 19.1 22 18V14C20.9 14 20 13.1 20 12S20.9 10 22 10Z" stroke="currentColor" stroke-width="2"/>
            </svg>
            Education
          </button>
        </div>

        <!-- Tab Content -->
        <div class="cv-tab-content">
          <transition name="fade" mode="out-in">
            <!-- Experience Tab -->
            <div v-if="activeTab === 'experience'" class="tab-panel" key="experience">
              <div class="timeline">
                <div 
                  v-for="(exp, index) in experience" 
                  :key="exp.id"
                  class="timeline-item"
                  :data-aos="index % 2 === 0 ? 'fade-right' : 'fade-left'"
                  :data-aos-delay="index * 100"
                >
                  <div class="timeline-marker"></div>
                  <div class="timeline-content">
                    <div class="timeline-header">
                      <h3 class="timeline-title">{{ exp.role }}</h3>
                      <span class="timeline-company">{{ exp.company }}</span>
                      <span class="timeline-period">{{ exp.period }}</span>
                    </div>
                    <p class="timeline-description">{{ exp.description }}</p>
                    <div class="timeline-skills">
                      <span v-for="skill in exp.skills" :key="skill" class="skill-tag">
                        {{ skill }}
                      </span>
                    </div>
                  </div>
                </div>
              </div>
            </div>

            <!-- Education Tab -->
            <div v-else class="tab-panel" key="education">
              <div class="timeline">
                <div 
                  v-for="(edu, index) in education" 
                  :key="edu.id"
                  class="timeline-item"
                  :data-aos="index % 2 === 0 ? 'fade-left' : 'fade-right'"
                  :data-aos-delay="index * 100"
                >
                  <div class="timeline-marker"></div>
                  <div class="timeline-content">
                    <div class="timeline-header">
                      <h3 class="timeline-title">{{ edu.degree }}</h3>
                      <span class="timeline-company">{{ edu.university }}</span>
                      <span class="timeline-period">{{ edu.period }}</span>
                    </div>
                    <p class="timeline-description">{{ edu.description }}</p>
                    <div class="timeline-skills" v-if="edu.achievements">
                      <span v-for="achievement in edu.achievements" :key="achievement" class="skill-tag">
                        {{ achievement }}
                      </span>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </transition>
        </div>

        <!-- Download CV Button -->
        <div class="cv-download" data-aos="fade-up" data-aos-delay="400">
          <button class="btn btn-primary download-btn" @click="downloadCV">
            <svg width="20" height="20" viewBox="0 0 24 24" fill="none">
              <path d="M21 15V19C21 19.5304 20.7893 20.0391 20.4142 20.4142C20.0391 20.7893 19.5304 21 19 21H5C4.46957 21 3.96086 20.7893 3.58579 20.4142C3.21071 20.0391 3 19.5304 3 19V15" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
              <polyline points="7,10 12,15 17,10" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
              <line x1="12" y1="15" x2="12" y2="3" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
            </svg>
            Download CV
          </button>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { ref } from 'vue'

interface ExperienceItem {
  id: number
  role: string
  company: string
  period: string
  description: string
  skills: string[]
}

interface EducationItem {
  id: number
  degree: string
  university: string
  period: string
  description: string
  achievements?: string[]
}

const activeTab = ref<'experience' | 'education'>('experience')

const experience = ref<ExperienceItem[]>([
  {
    id: 1,
    role: "Senior UI/UX Designer",
    company: "TechCorp Solutions",
    period: "2022 - Present",
    description: "Leading design initiatives for multiple products, mentoring junior designers, and establishing design systems that improved consistency across all platforms.",
    skills: ["Figma", "User Research", "Design Systems", "Prototyping"]
  },
  {
    id: 2,
    role: "UI/UX Designer",
    company: "Digital Innovations",
    period: "2020 - 2022",
    description: "Designed user interfaces for web and mobile applications, conducted user research, and collaborated with development teams to ensure pixel-perfect implementation.",
    skills: ["Sketch", "Adobe XD", "User Testing", "Wireframing"]
  },
  {
    id: 3,
    role: "Junior Designer",
    company: "Creative Studio",
    period: "2019 - 2020",
    description: "Assisted in creating visual designs for various clients, learned design principles, and contributed to brand identity projects.",
    skills: ["Photoshop", "Illustrator", "Brand Design", "Print Design"]
  }
])

const education = ref<EducationItem[]>([
  {
    id: 1,
    degree: "Master of Design",
    university: "Art & Design University",
    period: "2017 - 2019",
    description: "Specialized in Human-Computer Interaction and User Experience Design. Completed thesis on mobile app usability patterns.",
    achievements: ["Magna Cum Laude", "Design Excellence Award", "HCI Research"]
  },
  {
    id: 2,
    degree: "Bachelor of Fine Arts",
    university: "State University",
    period: "2013 - 2017",
    description: "Focused on Visual Communication Design with emphasis on digital media and interactive design principles.",
    achievements: ["Dean's List", "Student Design Competition Winner"]
  }
])

const setActiveTab = (tab: 'experience' | 'education') => {
  activeTab.value = tab
}

const downloadCV = () => {
  // Create a temporary link to trigger download
  const link = document.createElement('a')
  link.href = '/cv-kezia-designer.pdf' // This would be a static file in the public folder
  link.download = 'Kezia_Designer_CV.pdf'
  link.target = '_blank'
  document.body.appendChild(link)
  link.click()
  document.body.removeChild(link)
}
</script>

<style scoped>
.cv-section {
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

.cv-tabs {
  display: flex;
  justify-content: center;
  gap: 1rem;
  margin-bottom: 3rem;
}

.tab-button {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  padding: 1rem 2rem;
  background: transparent;
  color: var(--text-secondary);
  border: 2px solid var(--border-color);
  border-radius: 2rem;
  font-weight: 500;
  cursor: pointer;
  transition: all 0.3s ease;
  font-size: 1rem;
}

.tab-button:hover {
  color: var(--text-primary);
  border-color: var(--primary-purple);
}

.tab-button.active {
  background: var(--gradient-primary);
  color: white;
  border-color: transparent;
  box-shadow: var(--shadow-soft);
}

.cv-tab-content {
  margin-bottom: 3rem;
}

.timeline {
  position: relative;
  max-width: 900px;
  margin: 0 auto;
}

.timeline::before {
  content: '';
  position: absolute;
  left: 50%;
  top: 0;
  bottom: 0;
  width: 2px;
  background: var(--gradient-primary);
  transform: translateX(-50%);
}

.timeline-item {
  position: relative;
  margin-bottom: 3rem;
}

.timeline-item:nth-child(odd) .timeline-content {
  margin-left: 0;
  margin-right: 50%;
  padding-right: 2rem;
  text-align: right;
}

.timeline-item:nth-child(even) .timeline-content {
  margin-left: 50%;
  margin-right: 0;
  padding-left: 2rem;
  text-align: left;
}

.timeline-marker {
  position: absolute;
  left: 50%;
  top: 1rem;
  width: 16px;
  height: 16px;
  background: var(--gradient-primary);
  border: 4px solid var(--secondary-bg);
  border-radius: 50%;
  transform: translateX(-50%);
  z-index: 10;
  box-shadow: 0 0 0 4px rgba(168, 85, 247, 0.2);
}

.timeline-content {
  background: var(--gradient-card);
  border-radius: 1.5rem;
  padding: 2rem;
  border: 1px solid var(--border-color);
  backdrop-filter: blur(10px);
  transition: all 0.3s ease;
}

.timeline-content:hover {
  transform: translateY(-4px);
  box-shadow: var(--shadow-primary);
  border-color: var(--primary-purple);
}

.timeline-header {
  margin-bottom: 1rem;
}

.timeline-title {
  font-size: 1.4rem;
  font-weight: 600;
  color: var(--text-primary);
  margin-bottom: 0.5rem;
}

.timeline-company {
  display: block;
  font-size: 1.1rem;
  color: var(--secondary-purple);
  font-weight: 500;
  margin-bottom: 0.25rem;
}

.timeline-period {
  display: block;
  font-size: 0.9rem;
  color: var(--text-muted);
  text-transform: uppercase;
  letter-spacing: 0.05em;
}

.timeline-description {
  color: var(--text-secondary);
  line-height: 1.7;
  margin-bottom: 1rem;
}

.timeline-skills {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
}

.timeline-item:nth-child(odd) .timeline-skills {
  justify-content: flex-end;
}

.timeline-item:nth-child(even) .timeline-skills {
  justify-content: flex-start;
}

.skill-tag {
  padding: 0.25rem 0.75rem;
  background: var(--gradient-primary);
  color: white;
  border-radius: 1rem;
  font-size: 0.8rem;
  font-weight: 500;
}

.cv-download {
  text-align: center;
}

.download-btn {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  font-size: 1.1rem;
  padding: 1rem 2.5rem;
}

.download-btn:hover svg {
  transform: translateY(2px);
}

.fade-enter-active,
.fade-leave-active {
  transition: all 0.3s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
  transform: translateY(20px);
}

@media (max-width: 768px) {
  .timeline::before {
    left: 2rem;
  }

  .timeline-item:nth-child(odd) .timeline-content,
  .timeline-item:nth-child(even) .timeline-content {
    margin-left: 4rem;
    margin-right: 0;
    padding-left: 2rem;
    padding-right: 1.5rem;
    text-align: left;
  }

  .timeline-marker {
    left: 2rem;
  }

  .timeline-skills {
    justify-content: flex-start !important;
  }

  .cv-tabs {
    flex-direction: column;
    align-items: center;
    gap: 0.75rem;
  }

  .tab-button {
    width: 100%;
    max-width: 300px;
    justify-content: center;
  }

  .timeline-content {
    padding: 1.5rem;
  }
}
</style>
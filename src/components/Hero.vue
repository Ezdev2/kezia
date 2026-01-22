<template>
  <section id="hero">
    <div class="hero-grid">
      <div class="hero-text animated-border-box">
        <h1>
          Hey, I'm <span class="text-gradient">Kezia</span>, a web and mobile designer with
          <span class="text-gradient">5+ years</span> of experience.
        </h1>
        <p>
          I create beautiful, user-centered digital experiences that blend creativity with functionality. From elegant
          web interfaces to intuitive mobile apps, I bring ideas to life with passion and precision.
        </p>

        <div class="social-links">
          </div>
      </div>

      <div class="hero-image animated-border-box">
        <img src="https://images.pexels.com/photos/31708892/pexels-photo-31708892.jpeg?auto=compress&cs=tinysrgb&w=800"
          alt="Kezia - Senior Designer"/>
      </div>
    </div>
  </section>
</template>

<style scoped>
#hero {
  /* padding: 4rem 0; */
  height: 100vh;
  display: flex;
  align-items: center;
  --neon-purple: #a855f7;
  --neon-blue: #3b82f6;
}

.hero-grid {
  display: grid;
  grid-template-columns: 2fr 1fr;
  gap: 3rem;
  align-items: stretch;
  max-width: 1200px;
  margin: 80px auto;
  padding: 0 20px;
}

/* --- LE CONTOUR BRILLANT ANIMÉ --- */
.animated-border-box {
  position: relative;
  background: rgba(13, 17, 23, 0.6); 
  backdrop-filter: blur(20px);
  border-radius: 1.5rem;
  z-index: 1;
}

/* La bordure animée */
.animated-border-box::before {
  content: "";
  position: absolute;
  inset: -2px; /* Taille de la bordure */
  border-radius: 1.6rem;
  padding: 6px; /* Épaisseur */
  /* Dégradé de la bordure */
  background: conic-gradient(
    from 0deg,
    transparent 0%,
    var(--neon-purple) 25%,
    var(--neon-blue) 50%,
    transparent 75%
  );
  /* Masque pour ne garder que le contour */
  -webkit-mask: 
     linear-gradient(#fff 0 0) content-box, 
     linear-gradient(#fff 0 0);
  mask: 
     linear-gradient(#fff 0 0) content-box, 
     linear-gradient(#fff 0 0);
  -webkit-mask-composite: xor;
  mask-composite: exclude;
  
  /* Animation de tracé au début */
  animation: border-draw 4s cubic-bezier(0.25, 1, 0.5, 1) forwards;
  opacity: 0;
}

@keyframes border-draw {
  0% {
    opacity: 0;
    filter: hue-rotate(90deg);
  }
  100% {
    opacity: 1;
    filter: hue-rotate(0deg);
  }
}

/* --- CONTENU --- */
.hero-text {
  padding: 3rem;
  display: flex;
  flex-direction: column;
  justify-content: center;
}

.hero-text h1 {
  font-size: 3rem;
  font-weight: 800;
  line-height: 1.2;
  margin-bottom: 1.5rem;
  color: #fff;
}

.text-gradient {
  background: linear-gradient(to right, var(--neon-purple), var(--neon-blue));
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}

.hero-text p {
  font-size: 1.15rem;
  color: #94a3b8; /* Gris bleuté style Discord */
  line-height: 1.6;
  margin-bottom: 2.5rem;
}

/* Image */
.hero-image img {
  width: 100%;
  height: 100%;
  border-radius: 1.5rem;
  object-fit: cover;
  display: block;
}

/* Social links modernisés */
.social-links {
  display: flex;
  gap: 1.2rem;
}

.social-link {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 45px;
  height: 45px;
  background: rgba(255, 255, 255, 0.05);
  border: 1px solid rgba(255, 255, 255, 0.1);
  border-radius: 12px;
  color: #94a3b8;
  transition: all 0.3s ease;
}

.social-link:hover {
  background: rgba(168, 85, 247, 0.1);
  border-color: var(--neon-purple);
  color: #fff;
  transform: translateY(-3px);
  box-shadow: 0 10px 20px rgba(0, 0, 0, 0.2);
}

@media (max-width: 1024px) {
  .hero-grid {
    grid-template-columns: 1fr;
    text-align: center;
  }
  .hero-text { padding: 2rem; }
  .social-links { justify-content: center; }
}
</style>
<script lang="ts">
  const scrollToSection = (e: Event, target: string) => {
    e.preventDefault();
    const element = document.querySelector(target);
    if (element) {
      element.scrollIntoView({ behavior: 'smooth' });
    }
  };
</script>

<!-- Hero Section -->
<section class="hero">
  <div class="hero-bg"></div>
  
  <!-- Content -->
  <div class="hero-content">
    <h1 class="headline">
      I build reliable full-stack software systems with a strong backend foundation.
    </h1>
    <a href="#contact" class="cta-button" on:click={(e) => scrollToSection(e, '#contact')}>
      <span>Let's Work Together</span>
      <svg class="cta-arrow" width="16" height="16" viewBox="0 0 16 16" fill="none" xmlns="http://www.w3.org/2000/svg">
        <path d="M3 8H13M13 8L9 4M13 8L9 12" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
      </svg>
    </a>
  </div>

  <!-- Portrait -->
  <div class="hero-portrait">
    <img src="/mohammed-portrait.jpg" alt="Mohammed - Software Engineer" class="portrait-image">
  </div>

  <!-- Name Display -->
  <div class="name-display">
    <span class="name-text">Mohammed</span>
  </div>
</section>

<style>
  :global(html) {
    scroll-behavior: smooth;
  }

  /* Hero Section */
  .hero {
    position: relative;
    min-height: 100vh;
    width: 100%;
    display: grid;
    grid-template-columns: 1fr 1.2fr;
    overflow: hidden;
  }

  /* Background Gradient */
  .hero-bg {
    position: absolute;
    inset: 0;
    background: linear-gradient(135deg, #c17f45 0%, #a05a2c 40%, #1a1a1a 100%);
    z-index: 0;
  }

  .hero-bg::after {
    content: '';
    position: absolute;
    inset: 0;
    background: radial-gradient(ellipse at 30% 50%, transparent 0%, rgba(0,0,0,0.4) 100%);
  }

  /* Content Area */
  .hero-content {
    position: relative;
    z-index: 10;
    display: flex;
    flex-direction: column;
    justify-content: center;
    padding: 120px 48px 80px;
    max-width: 600px;
  }

  .headline {
    font-size: 32px;
    font-weight: 500;
    line-height: 1.35;
    color: #ffffff;
    margin-bottom: 32px;
    opacity: 0;
    transform: translateY(40px);
    animation: textReveal 1s cubic-bezier(0.16, 1, 0.3, 1) 0.4s forwards;
  }

  .cta-button {
    display: inline-flex;
    align-items: center;
    gap: 12px;
    padding: 16px 28px;
    background: rgba(255, 255, 255, 0.15);
    backdrop-filter: blur(10px);
    -webkit-backdrop-filter: blur(10px);
    border: 1px solid rgba(255, 255, 255, 0.2);
    border-radius: 50px;
    color: #ffffff;
    font-size: 14px;
    font-weight: 600;
    text-decoration: none;
    cursor: pointer;
    width: fit-content;
    opacity: 0;
    transform: translateY(20px);
    animation: buttonReveal 0.8s cubic-bezier(0.16, 1, 0.3, 1) 0.6s forwards;
    transition: all 0.3s cubic-bezier(0.16, 1, 0.3, 1);
  }

  .cta-button:hover {
    background: rgba(255, 255, 255, 0.25);
    transform: translateY(-2px);
    box-shadow: 0 8px 30px rgba(0, 0, 0, 0.2);
  }

  .cta-button:hover .cta-arrow {
    transform: translateX(4px);
  }

  .cta-arrow {
    transition: transform 0.3s cubic-bezier(0.16, 1, 0.3, 1);
  }

  /* Portrait Area */
  .hero-portrait {
    position: relative;
    z-index: 5;
    display: flex;
    align-items: flex-end;
    justify-content: center;
    padding-bottom: 0;
  }

  .portrait-image {
    width: 100%;
    height: 100%;
    object-fit: cover;
    object-position: center top;
    opacity: 0;
    transform: scale(1.02);
    animation: portraitReveal 1.5s cubic-bezier(0.16, 1, 0.3, 1) forwards;
  }

  /* Name Typography */
  .name-display {
    position: absolute;
    bottom: -20px;
    left: 0;
    right: 0;
    z-index: 20;
    text-align: center;
    pointer-events: none;
  }

  .name-text {
    font-size: clamp(100px, 18vw, 280px);
    font-weight: 800;
    letter-spacing: -0.03em;
    color: #ffffff;
    line-height: 0.85;
    opacity: 0;
    transform: scale(0.95);
    animation: nameReveal 1.2s cubic-bezier(0.16, 1, 0.3, 1) 0.3s forwards;
    text-shadow: 0 4px 60px rgba(0, 0, 0, 0.3);
  }

  /* Animations */
  @keyframes textReveal {
    from {
      opacity: 0;
      transform: translateY(40px);
    }
    to {
      opacity: 1;
      transform: translateY(0);
    }
  }

  @keyframes buttonReveal {
    from {
      opacity: 0;
      transform: translateY(20px);
    }
    to {
      opacity: 1;
      transform: translateY(0);
    }
  }

  @keyframes portraitReveal {
    from {
      opacity: 0;
      transform: scale(1.02);
    }
    to {
      opacity: 1;
      transform: scale(1);
    }
  }

  @keyframes nameReveal {
    from {
      opacity: 0;
      transform: scale(0.95);
    }
    to {
      opacity: 1;
      transform: scale(1);
    }
  }

  /* Responsive */
  @media (max-width: 1024px) {
    .hero {
      grid-template-columns: 1fr;
      grid-template-rows: auto 1fr;
    }

    .hero-content {
      padding: 140px 32px 40px;
      max-width: 100%;
      text-align: center;
      align-items: center;
    }

    .headline {
      font-size: 28px;
    }

    .hero-portrait {
      position: absolute;
      inset: 0;
      z-index: 1;
      opacity: 0.4;
    }

    .portrait-image {
      object-position: center;
    }

    .name-display {
      bottom: 40px;
    }

    .name-text {
      font-size: clamp(60px, 15vw, 150px);
    }


  }

  @media (max-width: 640px) {


    .headline {
      font-size: 24px;
    }

    .hero-content {
      padding: 120px 24px 40px;
    }
  }

  /* Reduced Motion */
  @media (prefers-reduced-motion: reduce) {
    *, *::before, *::after {
      animation-duration: 0.01ms !important;
      animation-iteration-count: 1 !important;
      transition-duration: 0.01ms !important;
    }
  }
</style>

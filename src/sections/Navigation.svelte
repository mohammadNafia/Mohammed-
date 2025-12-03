<script lang="ts">
  import { onMount } from 'svelte';
  import { Motion, AnimatePresence } from 'svelte-motion';
  import { Menu, X } from 'lucide-svelte';

  const navLinks = [
    { name: 'Services', href: '#services' },
    { name: 'Projects', href: '#projects' },
    { name: 'Process', href: '#process' },
    { name: 'Pricing', href: '#pricing' },
    { name: 'Contact', href: '#contact' },
  ];

  let scrollY = $state(0);
  let isMobileMenuOpen = $state(false);
  
  // Calculate navbar position based on scroll
  let navPosition = $derived.by(() => {
    const heroHeight = typeof window !== 'undefined' ? window.innerHeight : 1000;
    
    // In hero section (top of page) - center
    if (scrollY < heroHeight * 0.3) {
      return 'center';
    }
    // After scrolling past hero - right (and stays right for Services & beyond)
    else {
      return 'right';
    }
  });

  // Scroll handler
  onMount(() => {
    const handleScroll = () => {
      scrollY = window.scrollY;
    };
    
    handleScroll(); // Initial call
    window.addEventListener('scroll', handleScroll, { passive: true });
    return () => window.removeEventListener('scroll', handleScroll);
  });

  const scrollToSection = (href: string) => {
    const element = document.querySelector(href);
    if (element) {
      element.scrollIntoView({ behavior: 'smooth' });
    }
    isMobileMenuOpen = false;
  };

  const toggleMobileMenu = () => {
    isMobileMenuOpen = !isMobileMenuOpen;
  };
</script>

<!-- Desktop + Mobile Nav Bar -->
<Motion
  initial={{ y: -100, opacity: 0 }}
  animate={{ y: 0, opacity: 1 }}
  transition={{ duration: 0.6, ease: [0.16, 1, 0.3, 1] }}
  let:motion
>
  <nav
    use:motion
    class="fixed top-4 z-50 transition-all duration-700 ease-out rounded-full px-6 py-3"
    style="
      left: {navPosition === 'center' ? '50%' : navPosition === 'right' ? 'calc(100% - 20px)' : '20px'};
      transform: {navPosition === 'center' ? 'translateX(-50%)' : navPosition === 'right' ? 'translateX(-100%)' : 'translateX(0)'};
      width: {navPosition === 'center' ? '90%' : 'auto'};
      max-width: {navPosition === 'center' ? '48rem' : 'none'};
      background: {scrollY > 50 ? 'rgba(0, 0, 0, 0.8)' : 'rgba(255, 255, 255, 0.1)'};
      backdrop-filter: blur({scrollY > 50 ? '20px' : '10px'});
      border: 1px solid {scrollY > 50 ? 'rgba(255, 255, 255, 0.1)' : 'rgba(255, 255, 255, 0.2)'};
    "
  >
    <div class="flex items-center justify-between">
      <!-- Desktop Navigation -->
      <ul class="hidden md:flex items-center gap-8 {navPosition === 'center' ? 'mx-auto' : ''}">
        {#each navLinks as link, index (link.name)}
          <Motion
            initial={{ opacity: 0, y: -10 }}
            animate={{ opacity: 1, y: 0 }}
            transition={{ delay: 0.1 + index * 0.05, duration: 0.4 }}
            let:motion
          >
            <li use:motion>
              <button
                onclick={() => scrollToSection(link.href)}
                class="text-sm font-medium text-white/90 hover:text-white transition-colors relative group"
              >
                {link.name}
                <span class="absolute -bottom-1 left-0 w-0 h-0.5 bg-orange-500 transition-all duration-300 group-hover:w-full"></span>
              </button>
            </li>
          </Motion>
        {/each}
      </ul>

      <!-- Mobile Menu Button -->
      <button
        onclick={toggleMobileMenu}
        class="md:hidden text-white p-2"
      >
        {#if isMobileMenuOpen}
          <X size={24} />
        {:else}
          <Menu size={24} />
        {/if}
      </button>
    </div>
  </nav>
</Motion>

<!-- Mobile Menu Overlay -->
<AnimatePresence list={[{ key: isMobileMenuOpen ? 'open' : 'closed' }]}>
  {#if isMobileMenuOpen}
    <Motion
      initial={{ opacity: 0, y: -20 }}
      animate={{ opacity: 1, y: 0 }}
      exit={{ opacity: 0, y: -20 }}
      transition={{ duration: 0.3 }}
      let:motion
    >
      <div use:motion class="fixed inset-0 z-40 bg-black/95 backdrop-blur-xl pt-24 px-6 md:hidden">
        <ul class="flex flex-col items-center gap-6">
          {#each navLinks as link, index (link.name)}
            <Motion
              initial={{ opacity: 0, y: 20 }}
              animate={{ opacity: 1, y: 0 }}
              transition={{ delay: index * 0.1 }}
              let:motion
            >
              <li use:motion>
                <button
                  onclick={() => scrollToSection(link.href)}
                  class="text-2xl font-medium text-white/90 hover:text-orange-500 transition-colors"
                >
                  {link.name}
                </button>
              </li>
            </Motion>
          {/each}
        </ul>
      </div>
    </Motion>
  {/if}
</AnimatePresence>

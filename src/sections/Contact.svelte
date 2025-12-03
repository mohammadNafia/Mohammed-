<script lang="ts">
  import { Motion } from 'svelte-motion';
  import { Mail, Linkedin, Github, ArrowUpRight, Calendar } from 'lucide-svelte';
  import { fadeInUp, staggerContainer, blurReveal, bounceUp, staggerFast, floatIn } from '../animations/motion';

  const socialLinks = [
    { name: 'LinkedIn', icon: Linkedin, href: 'https://www.linkedin.com/in/mohammed-nafia-7b58141ba/' },
    { name: 'GitHub', icon: Github, href: 'https://github.com/mohammadNafia' },
  ];

  const navLinks = [
    { name: 'Projects', href: '#projects' },
    { name: 'Pricing', href: '#pricing' },
  ];

  const scrollToSection = (href: string) => {
    const element = document.querySelector(href);
    if (element) {
      element.scrollIntoView({ behavior: 'smooth' });
    }
  };
</script>

<svelte:head>
  <script src="https://asset-tidycal.b-cdn.net/js/embed.js" async></script>
</svelte:head>

<section id="contact" class="relative py-24 px-4 sm:px-6 lg:px-12 bg-black">
  <div class="max-w-7xl mx-auto">
    <!-- Main CTA -->
    <Motion
      variants={staggerFast}
      initial="hidden"
      whileInView="visible"
      viewport={{ once: true, margin: '-100px' }}
      let:motion
    >
      <div use:motion class="text-center mb-20">
        <Motion variants={blurReveal} let:motion>
          <h2 use:motion class="text-4xl sm:text-5xl lg:text-7xl font-bold text-white mb-6">
            Book a
            <br />
            Free Call
          </h2>
        </Motion>
        <Motion variants={floatIn} let:motion>
          <p use:motion class="text-white/60 text-lg mb-10">
            Let's Create Something Amazing – Book a Session Now!
          </p>
        </Motion>

        <!-- Calendar Embed Placeholder -->
        <Motion variants={bounceUp} let:motion>
          <div use:motion class="relative max-w-3xl mx-auto">
            <div class="bg-zinc-900 rounded-3xl overflow-hidden border border-white/5">
              <div class="grid grid-cols-1 lg:grid-cols-3">
                <!-- Left side - Info -->
                <div class="p-8 bg-zinc-950 border-b lg:border-b-0 lg:border-r border-white/5">
                  <div class="flex items-center gap-3 mb-6">
                    <div class="w-10 h-10 rounded-full overflow-hidden flex items-center justify-center border border-white/10">
                      <!-- Using the image from the screenshot as a reference, assuming user wants their own avatar or a placeholder -->
                      <img src="/mohammed-portrait.jpg" alt="Profile" class="w-full h-full object-cover">
                    </div>
                    <span class="text-white font-medium">Mohammed Nafia</span>
                  </div>
                  <h3 class="text-2xl font-bold text-white mb-4">
                    Let's Chat About Your Idea
                  </h3>
                  <p class="text-white/60 text-sm leading-relaxed mb-6">
                    Building software systems shouldn’t be stressful. Let’s have a casual 1-on-1 chat about your product, architecture, and technical needs.
                  </p>
                  <div class="flex items-center gap-2 text-white/50 text-sm">
                    <span class="w-4 h-4 flex items-center justify-center rounded-full border border-white/20">
                      <div class="w-2 h-2 bg-white/50 rounded-full"></div>
                    </span>
                    30 minutes
                  </div>
                </div>

                <!-- Right side - Calendar -->
                <div class="lg:col-span-2 bg-zinc-900 border-l border-white/5 h-96 overflow-y-auto">
                  <div class="tidycal-embed w-full" data-path="mohammadnafia1/30-minute-meeting"></div>
                </div>
              </div>
            </div>
          </div>
        </Motion>
      </div>
    </Motion>

    <!-- Footer -->
    <Motion
      variants={staggerContainer}
      initial="hidden"
      whileInView="visible"
      viewport={{ once: true, margin: '-100px' }}
      let:motion
    >
      <footer use:motion class="border-t border-white/5 pt-16">
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-12 mb-16">
          <!-- Inquiries -->
          <Motion variants={fadeInUp} let:motion>
            <div use:motion>
              <h4 class="text-white/40 text-sm font-medium mb-4 uppercase tracking-wider">
                (Inquiries)
              </h4>
              <a
                href="mailto:mohammadnafia1@gmail.com"
                class="text-white hover:text-orange-500 transition-colors flex items-center gap-2"
              >
                <Mail class="w-4 h-4" />
                mohammadnafia1@gmail.com
              </a>
            </div>
          </Motion>

          <!-- Socials -->
          <Motion variants={fadeInUp} let:motion>
            <div use:motion>
              <h4 class="text-white/40 text-sm font-medium mb-4 uppercase tracking-wider">
                (socials)
              </h4>
              <ul class="space-y-3">
                {#each socialLinks as link (link.name)}
                  <li>
                    <a
                      href={link.href}
                      target="_blank"
                      rel="noopener noreferrer"
                      class="text-white hover:text-orange-500 transition-colors flex items-center gap-2"
                    >
                      <link.icon class="w-4 h-4" />
                      {link.name}
                    </a>
                  </li>
                {/each}
              </ul>
            </div>
          </Motion>

          <!-- Navigation -->
          <Motion variants={fadeInUp} let:motion>
            <div use:motion>
              <h4 class="text-white/40 text-sm font-medium mb-4 uppercase tracking-wider">
                (navigation)
              </h4>
              <ul class="space-y-3">
                {#each navLinks as link (link.name)}
                  <li>
                    <button
                      onclick={() => scrollToSection(link.href)}
                      class="text-white hover:text-orange-500 transition-colors"
                    >
                      {link.name}
                    </button>
                  </li>
                {/each}
                <li>
                  <a
                    href="https://tidycal.com/mohammadnafia1/30-minute-meeting"
                    target="_blank"
                    rel="noopener noreferrer"
                    class="text-white hover:text-orange-500 transition-colors"
                  >
                    Book a Call
                  </a>
                </li>
              </ul>
            </div>
          </Motion>

          <!-- Brand -->
          <Motion variants={fadeInUp} let:motion>
            <div use:motion class="lg:text-right">
              <h3 class="text-6xl sm:text-7xl font-black text-white/10 hover:text-white/20 transition-colors cursor-default">
                Mohammed
              </h3>
            </div>
          </Motion>
        </div>

        <!-- Copyright -->
        <Motion variants={fadeInUp} let:motion>
          <div use:motion class="text-center pt-8 border-t border-white/5">
            <p class="text-white/30 text-sm">
              © 2025 Mohammed. All rights reserved.
            </p>
          </div>
        </Motion>
      </footer>
    </Motion>
  </div>
</section>

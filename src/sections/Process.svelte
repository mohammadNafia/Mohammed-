<script lang="ts">
  import { Motion } from 'svelte-motion';
  import { MessageSquare, Layout, Code2, Rocket, Heart, Search } from 'lucide-svelte';
  import { fadeInUp, staggerContainer, blurReveal, boxPopIn, staggerFast, floatIn } from '../animations/motion';

  const steps = [
    {
      number: '01',
      icon: Search,
      title: 'Discovery & Requirements',
      description: 'We start by understanding the problem, business goals, and system requirements. This phase focuses on defining core features, identifying constraints, and aligning technical decisions with real-world use cases before writing any code.',
    },
    {
      number: '02',
      icon: Layout,
      title: 'System Design & UI Planning',
      description: 'I design the system architecture, data models, and API structure while also planning the frontend structure and user experience. This step includes defining UI flows, component responsibilities, and how the frontend communicates with the backend through well-defined API contracts.',
    },
    {
      number: '03',
      icon: Code2,
      title: 'Development & Implementation',
      description: 'I implement the system using modern engineering practices, focusing on clean code, reliable APIs, and secure backend logic. Frontend and backend are developed with clear boundaries, ensuring consistent UI behavior, performance, and reliable data flow across the application.',
    },
    {
      number: '04',
      icon: Rocket,
      title: 'Testing, Delivery & Iteration',
      description: 'The system is tested, reviewed, and prepared for deployment. I ensure stability, performance, and a smooth handover, with the ability to iterate and evolve the system as requirements grow.',
    },
  ];
</script>

<section id="process" class="relative py-24 px-4 sm:px-6 lg:px-12 bg-black">
  <div class="max-w-7xl mx-auto">
    <!-- Section Header -->
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
            Process is
            <br />
            Everything
          </h2>
        </Motion>
        <Motion variants={floatIn} let:motion>
          <p use:motion class="text-white/60 text-lg max-w-xl mx-auto">
            A structured engineering process that turns ideas into scalable, reliable software systems.
          </p>
        </Motion>
      </div>
    </Motion>

    <!-- Process Steps -->
    <Motion
      variants={staggerFast}
      initial="hidden"
      whileInView="visible"
      viewport={{ once: true, margin: '-100px' }}
      let:motion
    >
      <div use:motion class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-6">
        {#each steps as step, index (step.number)}
          <Motion variants={boxPopIn} let:motion>
            <div use:motion class="group relative">
              <div class="relative bg-gradient-to-br from-zinc-900 to-zinc-950 rounded-3xl p-8 h-full border border-white/5 hover:border-orange-500/30 transition-all duration-500 overflow-hidden">
                <!-- Gradient overlay -->
                <div class="absolute inset-0 bg-gradient-to-br from-orange-500/5 to-transparent opacity-0 group-hover:opacity-100 transition-opacity duration-500"></div>
                
                <!-- Content -->
                <div class="relative z-10">
                  <!-- Step number -->
                  <div class="flex items-center justify-between mb-6">
                    <span class="text-5xl font-black text-white/10 group-hover:text-orange-500/20 transition-colors">
                      {step.number}
                    </span>
                    <div class="w-12 h-12 rounded-2xl bg-orange-500/10 flex items-center justify-center group-hover:bg-orange-500/20 transition-colors">
                      <step.icon class="w-6 h-6 text-orange-500" />
                    </div>
                  </div>

                  <!-- Title -->
                  <h3 class="text-xl font-semibold text-white mb-4 group-hover:text-orange-500 transition-colors">
                    {step.title}
                  </h3>

                  <!-- Description -->
                  <p class="text-white/50 text-sm leading-relaxed">
                    {step.description}
                  </p>
                </div>

                <!-- Connection line -->
                {#if index < steps.length - 1}
                  <div class="hidden lg:block absolute top-1/2 -right-3 w-6 h-px bg-gradient-to-r from-white/20 to-transparent"></div>
                {/if}
              </div>
            </div>
          </Motion>
        {/each}
      </div>
    </Motion>

    <!-- Bottom message -->
    <Motion
      initial={{ opacity: 0, y: 30 }}
      whileInView={{ opacity: 1, y: 0 }}
      transition={{ delay: 0.6, duration: 0.6 }}
      viewport={{ once: true }}
      let:motion
    >
      <div use:motion class="mt-16 text-center">
        <div class="inline-flex items-center gap-3 px-6 py-3 bg-zinc-900/50 rounded-full border border-white/5">
          <Heart class="w-5 h-5 text-orange-500 fill-orange-500" />
          <span class="text-white/70 text-sm">
            I focus on building software that is reliable, maintainable, and designed to scale not just shipped fast.
          </span>
        </div>
      </div>
    </Motion>
  </div>
</section>

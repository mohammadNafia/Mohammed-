<script lang="ts">
  import { Motion } from 'svelte-motion';
  import { Check, ArrowUpRight, Sparkles } from 'lucide-svelte';
  import { fadeInUp, staggerContainer, blurReveal, bounceUp, staggerFast } from '../animations/motion';

  const plans = [
    {
      name: 'Full-Stack Applications',
      subtitle: '(MVP to Production)',
      price: 'Custom',
      description: 'Building full-stack web applications with a strong backend foundation — from early-stage MVPs to production-ready systems.',
      features: [
        'Clean REST APIs',
        'Secure Authentication',
        'Database Design',
        'Modern Frontends',
        'Scalable Architecture',
        'Maintainable Code',
      ],
      cta: 'Contact Me',
      popular: true,
    },
    {
      name: 'System Design & Technical Guidance',
      subtitle: '',
      price: 'Hourly / Project',
      description: 'Providing technical guidance during planning and development phases.',
      features: [
        'System Architecture',
        'API Structure',
        'Data Modeling',
        'Technical Decision Making',
      ],
      cta: 'Book a Call',
      popular: false,
    },
  ];

  const scrollToContact = () => {
    const element = document.querySelector('#contact');
    if (element) {
      element.scrollIntoView({ behavior: 'smooth' });
    }
  };
</script>

<section id="pricing" class="relative py-24 px-4 sm:px-6 lg:px-12 bg-black">
  <div class="max-w-7xl mx-auto">
    <!-- Section Header -->
    <Motion
      variants={staggerFast}
      initial="hidden"
      whileInView="visible"
      viewport={{ once: true, margin: '-100px' }}
      let:motion
    >
      <div use:motion class="text-center mb-16">
        <Motion variants={blurReveal} let:motion>
          <h2 use:motion class="text-4xl sm:text-5xl lg:text-6xl font-bold text-white mb-6">
            How I Work
            <br />
            With Projects
          </h2>
        </Motion>
        <Motion variants={bounceUp} let:motion>
          <p use:motion class="text-white/60 text-lg max-w-2xl mx-auto whitespace-pre-line">
            Every project is different. I focus on understanding the problem, scope, and technical requirements first, then choosing the right approach to build a reliable and scalable solution.

            Open to full-time roles and selective freelance projects.
          </p>
        </Motion>
      </div>
    </Motion>

    <!-- Pricing Cards -->
    <Motion
      variants={staggerFast}
      initial="hidden"
      whileInView="visible"
      viewport={{ once: true, margin: '-100px' }}
      let:motion
    >
      <div use:motion class="grid grid-cols-1 lg:grid-cols-2 gap-8 max-w-4xl mx-auto">
        {#each plans as plan (plan.name)}
          <Motion variants={bounceUp} let:motion>
            <div use:motion class={`group relative rounded-3xl overflow-hidden ${
              plan.popular
                ? 'bg-gradient-to-br from-orange-500/20 to-orange-600/10 border-2 border-orange-500/50'
                : 'bg-gradient-to-br from-zinc-900 to-zinc-950 border border-white/5 hover:border-white/20'
            } transition-all duration-500`}>
              <!-- Popular badge -->
              {#if plan.popular}
                <div class="absolute top-4 right-4 flex items-center gap-1 px-3 py-1 bg-orange-500 rounded-full">
                  <Sparkles class="w-3 h-3 text-white" />
                  <span class="text-xs font-medium text-white">Popular</span>
                </div>
              {/if}

              <div class="p-8">
                <!-- Plan name -->
                <h3 class="text-xl font-semibold text-white mb-1">{plan.name}</h3>
                {#if plan.subtitle}
                  <span class="text-orange-500 text-sm font-medium mb-4 block">{plan.subtitle}</span>
                {/if}
                
                <!-- Price (Hidden or Modified) -->
                <!-- <div class="flex items-baseline gap-1 mb-4">
                  <span class="text-4xl sm:text-5xl font-bold text-white">{plan.price}</span>
                </div> -->

                <!-- Description -->
                <p class="text-white/60 text-sm mb-8">{plan.description}</p>

                <!-- Features -->
                <ul class="space-y-4 mb-8">
                  {#each plan.features as feature}
                    <li key={feature} class="flex items-center gap-3">
                      <div class={`w-5 h-5 rounded-full flex items-center justify-center ${
                        plan.popular ? 'bg-orange-500' : 'bg-white/10'
                      }`}>
                        <Check class={`w-3 h-3 ${plan.popular ? 'text-white' : 'text-orange-500'}`} />
                      </div>
                      <span class="text-white/80 text-sm">{feature}</span>
                    </li>
                  {/each}
                </ul>

                <!-- CTA Button -->
                <button
                  onclick={scrollToContact}
                  class={`w-full group/btn flex items-center justify-center gap-2 py-4 rounded-full font-medium transition-all duration-300 ${
                    plan.popular
                      ? 'bg-orange-500 hover:bg-orange-600 text-white'
                      : 'bg-white/10 hover:bg-white/20 text-white border border-white/20'
                  }`}
                >
                  {plan.cta}
                  <ArrowUpRight class="w-4 h-4 group-hover/btn:translate-x-0.5 group-hover/btn:-translate-y-0.5 transition-transform" />
                </button>
              </div>
            </div>
          </Motion>
        {/each}
      </div>
    </Motion>

    <!-- Custom Quote -->
    <Motion
      initial={{ opacity: 0, y: 30 }}
      whileInView={{ opacity: 1, y: 0 }}
      transition={{ delay: 0.5, duration: 0.6 }}
      viewport={{ once: true }}
      let:motion
    >
      <div use:motion class="mt-12 text-center">
        <div class="inline-flex flex-col sm:flex-row items-center gap-4 p-6 bg-zinc-900/50 rounded-3xl border border-white/5">
          <div class="flex items-center gap-3">
            <div class="w-10 h-10 rounded-full bg-orange-500/20 flex items-center justify-center">
              <Sparkles class="w-5 h-5 text-orange-500" />
            </div>
            <span class="text-white font-medium">Custom Quote</span>
          </div>
          <p class="text-white/50 text-sm max-w-md">
            Once I understand the scope, I’ll propose options so you can choose what fits your budget and timeline.
          </p>
          <button
            onclick={scrollToContact}
            class="flex items-center gap-2 px-6 py-3 bg-white/10 hover:bg-white/20 rounded-full text-white text-sm font-medium transition-colors"
          >
            Contact Me
            <ArrowUpRight class="w-4 h-4" />
          </button>
        </div>
      </div>
    </Motion>
  </div>
</section>

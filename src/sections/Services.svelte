<script lang="ts">
  import { Motion } from 'svelte-motion';
  /* New Icons */
  import { 
    Server, Network, Lock, Layers, Database, Repeat, Gauge, Sliders, Boxes, Plug,
    ArrowUpRight, Globe, Bot, MessageSquare, Layout, Code, Smartphone
  } from 'lucide-svelte';
  import { fadeInUp, staggerContainer, bounceUp, blurReveal, boxPopIn, staggerFast } from '../animations/motion';

  const skills = [
    { name: 'Backend Development', icon: Server },
    { name: 'REST API Design', icon: Network },
    { name: 'Authentication & Authorization', icon: Lock },
    { name: 'Clean Architecture', icon: Layers },

    { name: 'Database Design', icon: Database },
    { name: 'Entity Framework Core', icon: Database },
    { name: 'Transactional Systems', icon: Repeat },
    { name: 'Caching & Performance', icon: Gauge },

    { name: 'Frontend Development', icon: Layout },
    { name: 'React & TypeScript', icon: Code },
    { name: 'UI State Management', icon: Sliders },
    { name: 'Responsive Interfaces', icon: Smartphone },

    { name: 'System Design', icon: Boxes },
    { name: 'API Integration', icon: Plug },
  ];

  const scrollToContact = () => {
    const element = document.querySelector('#contact');
    if (element) {
      element.scrollIntoView({ behavior: 'smooth' });
    }
  };
</script>

<section id="services" class="relative py-24 px-4 sm:px-6 lg:px-12 bg-black">
  <!-- Section Header -->
  <div class="max-w-7xl mx-auto mb-16">
    <Motion
      variants={staggerFast}
      initial="hidden"
      whileInView="visible"
      viewport={{ once: true, margin: "-100px" }}
      let:motion
    >
      <div use:motion class="flex flex-col sm:flex-row sm:items-end sm:justify-between gap-6">
        <Motion variants={blurReveal} let:motion>
          <h2 use:motion class="text-4xl sm:text-5xl lg:text-6xl font-bold text-white leading-tight">
            What I Build
            <br />
            <span class="justify-center items-center text-orange-500">&</span>
            <br />
            How I Work
          </h2>
        </Motion>

        <Motion variants={bounceUp} let:motion>
          <button
            use:motion
            onclick={scrollToContact}
            class="group flex items-center gap-2 self-start sm:self-auto bg-white/10 hover:bg-white/20 backdrop-blur-sm border border-white/30 rounded-full px-6 py-3 text-white font-medium transition-all duration-300"
          >
            Get in Touch
            <span class="flex items-center justify-center w-8 h-8 bg-white rounded-full text-black group-hover:scale-110 transition-transform">
              <ArrowUpRight size={16} />
            </span>
          </button>
        </Motion>
      </div>
    </Motion>
  </div>

  <!-- Services Grid -->
  <div class="max-w-7xl mx-auto">
    <Motion
      variants={staggerFast}
      initial="hidden"
      whileInView="visible"
      viewport={{ once: true, margin: "-100px" }}
      let:motion
    >
      <div use:motion class="grid grid-cols-1 lg:grid-cols-3 gap-6">
        <!-- Service Card 1 - Large with image -->
        <Motion variants={boxPopIn} let:motion>
          <div use:motion class="lg:col-span-2 group relative bg-gradient-to-br from-zinc-900 to-zinc-950 rounded-3xl overflow-hidden border border-white/5 hover:border-orange-500/30 transition-all duration-500">
            <div class="p-8 pb-0">
              <div class="flex items-center gap-3 mb-4">
                <div class="w-10 h-10 rounded-xl bg-orange-500/20 flex items-center justify-center">
                  <Globe class="w-5 h-5 text-orange-500" />
                </div>
                <h3 class="text-xl font-semibold text-white">Website Design & Development</h3>
              </div>
              <p class="text-white/60 text-sm leading-relaxed max-w-md mb-6">
                I design and develop modern, high-quality websites and web applications using a full-stack approach. This includes building clean and responsive frontends, designing robust backend APIs, and ensuring seamless communication between the client and the server. My goal is to deliver fast, scalable, and maintainable web solutions that are built with real business needs in mind  not just visual design.
              </p>
            </div>
            <div class="relative h-64 mx-4 mb-4 rounded-2xl overflow-hidden">
              <img
                src="https://images.unsplash.com/photo-1460925895917-afdab827c52f?w=800&q=80"
                alt="Website Design"
                class="w-full h-full object-cover group-hover:scale-105 transition-transform duration-700"
              />
              <div class="absolute inset-0 bg-gradient-to-t from-zinc-950 via-transparent to-transparent"></div>
            </div>
          </div>
        </Motion>

        <!-- Service Card 2 - Text only -->
        <Motion variants={boxPopIn} let:motion>
          <div use:motion class="group relative bg-gradient-to-br from-zinc-900 to-zinc-950 rounded-3xl p-8 border border-white/5 hover:border-orange-500/30 transition-all duration-500">
            <div class="flex items-center gap-3 mb-4">
              <div class="w-10 h-10 rounded-xl bg-orange-500/20 flex items-center justify-center">
                <MessageSquare class="w-5 h-5 text-orange-500" />
              </div>
              <h3 class="text-xl font-semibold text-white">Strategy & Technical Consulting</h3>
            </div>
            <p class="text-white/60 text-sm leading-relaxed">
              I provide technical consulting for startups, teams, and individuals who need clarity on software architecture, system design, and technical direction. Whether you are planning a new product, refactoring an existing system, or choosing the right technologies, I help you make informed engineering decisions based on scalability, security, and maintainability.
            </p>
          </div>
        </Motion>

        <!-- Service Card 3 - With image -->
        <Motion variants={boxPopIn} let:motion>
          <div use:motion class="lg:col-span-3 group relative bg-gradient-to-br from-zinc-900 to-zinc-950 rounded-3xl overflow-hidden border border-white/5 hover:border-orange-500/30 transition-all duration-500">
            <div class="grid grid-cols-1 lg:grid-cols-2 gap-8">
              <div class="p-8 flex flex-col justify-center">
                <div class="flex items-center gap-3 mb-4">
                  <div class="w-10 h-10 rounded-xl bg-orange-500/20 flex items-center justify-center">
                    <Bot class="w-5 h-5 text-orange-500" />
                  </div>
                  <h3 class="text-xl font-semibold text-white">Software Systems & AI Development</h3>
                </div>
                <p class="text-white/60 text-sm leading-relaxed">
                  I design and build backend-heavy software systems such as internal platforms, management systems, and large-scale business applications. This includes system architecture, database design, authentication and authorization, workflow automation, and integration with AI or external services. I focus on building reliable, extensible systems that can grow with the company and support real operational workflows.
                </p>
              </div>
              <div class="relative h-64 lg:h-auto m-4 rounded-2xl overflow-hidden">
                <img
                  src="https://images.unsplash.com/photo-1677442136019-21780ecad995?w=800&q=80"
                  alt="AI Automations"
                  class="w-full h-full object-cover group-hover:scale-105 transition-transform duration-700"
                />
                <div class="absolute inset-0 bg-gradient-to-r from-zinc-950 via-transparent to-transparent lg:bg-gradient-to-l"></div>
              </div>
            </div>
          </div>
        </Motion>
      </div>
    </Motion>

    <!-- Skills Marquee -->
    <Motion
      initial={{ opacity: 0 }}
      whileInView={{ opacity: 1 }}
      viewport={{ once: true }}
      transition={{ delay: 0.5, duration: 0.6 }}
      let:motion
    >
      <div use:motion class="mt-16 overflow-hidden">
        <div class="flex animate-marquee whitespace-nowrap">
          {#each [...skills, ...skills] as skill, index}
            <div
              key={index}
              class="flex items-center gap-2 mx-4 px-4 py-2 bg-zinc-900/50 rounded-full border border-white/5"
            >
              <skill.icon class="w-4 h-4 text-orange-500" />
              <span class="text-sm text-white/70">{skill.name}</span>
            </div>
          {/each}
        </div>
      </div>
    </Motion>
  </div>
</section>

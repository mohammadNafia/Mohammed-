<script lang="ts">
  import { Motion } from 'svelte-motion';
  import { fadeInUp, staggerContainer, blurReveal, slideLeftBounce, slideRightBounce, staggerFast } from '../animations/motion';

  const projects = [
    {
      id: 1,
      name: 'Rent-A-Ride',
      category: 'Full-Stack',
      tags: ['ASP.NET Core', 'React', 'Clean Architecture'],
      image: 'https://images.unsplash.com/photo-1503376780353-7e6692767b70?w=1200&q=80',
      description: 'A production-ready full-stack car rental platform built with a backend-first architecture. The system exposes a robust RESTful API using Clean Architecture, handling authentication, vehicle management, rental workflows, maintenance, and amenities. Advanced backend patterns are applied, including JWT-based role authorization, EF Core interceptors for audit logging, soft delete, caching, and pagination. A React frontend consumes the API to deliver a clean and responsive user experience.',
      techStack: 'ASP.NET Core (.NET 8), EF Core, SQL Server, JWT, Clean Architecture, REST APIs, React',
    },
    {
      id: 2,
      name: 'Cinema Booking & Management System',
      category: 'Full-Stack',
      tags: ['ASP.NET Core', 'React', 'TypeScript'],
      image: 'https://images.unsplash.com/photo-1489599849927-2ee91cede3ba?w=800&q=80',
      description:'A full-stack cinema booking system designed to handle real-world booking constraints such as concurrent reservations, seat availability validation, and transactional consistency. The backend enforces double-booking prevention at both application and database levels and integrates with the IMDb API through a backend-only, cached service for performance and security. A React frontend provides a clear booking flow for browsing movies, selecting seats, and completing reservations.',

  techStack: 'ASP.NET Core, EF Core, SQL Server, REST APIs, IMDb API, React, TypeScript',
    },
    {
      id: 3,
      name: 'Library Management System',
      category: 'Backend-Only',
      tags: ['ASP.NET Core', 'Clean Architecture', 'JWT'],
      image: 'https://images.unsplash.com/photo-1555066931-4365d14bab8c?w=800&q=80',
      description:'A backend-only library management system built with ASP.NET Core Web API following Clean Architecture principles. The system implements JWT authentication without ASP.NET Identity, role-based authorization, custom middleware, soft delete with global query filters, and audit logging. This project focuses on demonstrating deep backend engineering practices without frontend abstractions.',

      techStack: 'ASP.NET Core, EF Core, PostgreSQL / SQL Server, JWT, Clean Architecture, REST APIs',
    },
  ];
</script>

<section id="projects" class="relative py-24 px-4 sm:px-6 lg:px-12 bg-black overflow-hidden">
  <!-- Background text -->
  <div class="absolute inset-0 flex items-center justify-center pointer-events-none overflow-hidden">
    <Motion
      initial={{ x: '0%' }}
      animate={{ x: '-50%' }}
      transition={{ duration: 30, repeat: Infinity, ease: 'linear' }}
      let:motion
    >
      <div use:motion class="flex whitespace-nowrap">
        {#each Array(4) as _, i}
          <span
            key={i}
            class="text-[20vw] font-black text-white/[0.02] mx-8 select-none"
          >
            RGM PARTNERS
          </span>
        {/each}
      </div>
    </Motion>
  </div>

  <div class="relative z-10 max-w-7xl mx-auto">
    <!-- Section Header -->
    <Motion
      variants={staggerFast}
      initial="hidden"
      whileInView="visible"
      viewport={{ once: true, margin: '-100px' }}
      let:motion
    >
      <div use:motion class="mb-16">
        <Motion variants={blurReveal} let:motion>
          <h2 use:motion class="text-4xl sm:text-5xl lg:text-6xl font-bold text-white">
            Recent
            <br />
            Projects
          </h2>
        </Motion>
      </div>
    </Motion>

    <!-- Projects Grid -->
    <Motion
      variants={staggerFast}
      initial="hidden"
      whileInView="visible"
      viewport={{ once: true, margin: '-100px' }}
      let:motion
    >
      <div use:motion class="space-y-8">
        {#each projects as project, index (project.id)}
          <Motion variants={index % 2 === 0 ? slideLeftBounce : slideRightBounce} let:motion>
            <div use:motion class="group relative">
              <div class={`grid grid-cols-1 lg:grid-cols-2 gap-8 items-center ${
                index % 2 === 1 ? 'lg:flex-row-reverse' : ''
              }`}>
                <!-- Image -->
                <div class={`relative overflow-hidden rounded-3xl ${
                  index % 2 === 1 ? 'lg:order-2' : ''
                }`}>
                  <div class="aspect-[16/10] overflow-hidden">
                    <img
                      src={project.image}
                      alt={project.name}
                      class="w-full h-full object-cover group-hover:scale-105 transition-transform duration-700"
                    />
                  </div>
                  <!-- Overlay -->
                  <div class="absolute inset-0 bg-gradient-to-t from-black/60 via-transparent to-transparent"></div>
                  
                  <!-- Project info on image -->
                  <div class="absolute bottom-6 left-6 right-6">
                    <div class="flex items-center gap-2 mb-2">
                      {#each project.tags as tag}
                        <span
                          class="px-3 py-1 text-xs font-medium text-white/80 bg-white/10 backdrop-blur-sm rounded-full"
                        >
                          {tag}
                        </span>
                      {/each}
                    </div>
                  </div>
                </div>

                <!-- Content -->
                <div class={`${index % 2 === 1 ? 'lg:order-1' : ''}`}>
                  <Motion
                    initial={{ opacity: 0, x: index % 2 === 1 ? 40 : -40 }}
                    whileInView={{ opacity: 1, x: 0 }}
                    transition={{ duration: 0.6, delay: 0.2 }}
                    viewport={{ once: true }}
                    let:motion
                  >
                    <div use:motion>
                      <span class="text-orange-500 text-sm font-medium mb-2 block">
                        {project.category}
                      </span>
                      <h3 class="text-3xl sm:text-4xl font-bold text-white mb-4 group-hover:text-orange-500 transition-colors">
                        {project.name}
                      </h3>
                      <p class="text-white/60 leading-relaxed mb-4">
                        {project.description}
                      </p>
                      {#if project.techStack}
                        <div class="mt-4 pt-4 border-t border-white/10">
                          <p class="text-white/40 text-xs font-medium mb-2">Tech Stack</p>
                          <p class="text-white/50 text-sm">
                            {project.techStack}
                          </p>
                        </div>
                      {/if}
                    </div>
                  </Motion>
                </div>
              </div>

              <!-- Divider -->
              {#if index < projects.length - 1}
                <Motion
                  initial={{ scaleX: 0 }}
                  whileInView={{ scaleX: 1 }}
                  transition={{ duration: 0.8, delay: 0.3 }}
                  viewport={{ once: true }}
                  let:motion
                >
                  <div use:motion class="h-px bg-gradient-to-r from-transparent via-white/10 to-transparent mt-8 origin-left"></div>
                </Motion>
              {/if}
            </div>
          </Motion>
        {/each}
      </div>
    </Motion>
  </div>
</section>

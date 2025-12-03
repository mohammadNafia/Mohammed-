<script lang="ts">
  import Navigation from './sections/Navigation.svelte';
  import Hero from './sections/Hero.svelte';
  import Services from './sections/Services.svelte';
  import Projects from './sections/Projects.svelte';
  import Process from './sections/Process.svelte';
  import Pricing from './sections/Pricing.svelte';
  import Contact from './sections/Contact.svelte';
</script>

<div class="min-h-screen bg-black text-white overflow-x-hidden">
  <Navigation></Navigation>
  <main>
    <Hero></Hero>
    <Services></Services>
    <Projects></Projects>
    <Process></Process>
    <Pricing></Pricing>
    <Contact></Contact>
  </main>
</div>

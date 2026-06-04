<template>
  <div class="min-h-screen bg-[#1c2c26] text-[#e4e4e0] font-sans">
    <header class="min-h-screen flex flex-col justify-between p-8 md:p-12 border-b border-[#b88c4c]/20">
      <div>
        <h2 class="text-lg font-bold uppercase">{{ devData.name }}</h2>
        <p class="text-xs text-[#b88c4c] uppercase mt-1">{{ devData.role }}</p>
      </div>

      <div class="flex flex-col md:flex-row gap-12 items-center md:items-end">
        <div class="flex-1">
          <h1 class="text-5xl md:text-6xl font-black uppercase leading-tight mb-6">Portfolio.</h1>
          <p class="text-sm text-gray-400 max-w-md">{{ devData.bio }}</p>
        </div>

        <!-- FIXED IMAGE PATH -->
        <img
          :src="devData.photo"
          :alt="devData.name"
          class="w-48 h-48 rounded-lg object-cover border border-[#b88c4c]/30"
        >
      </div>

      <div class="flex justify-between items-end">
        <div class="text-xs text-gray-400">
          <p>{{ devData.website }}</p>
          <p class="text-[#b88c4c] mt-1">{{ devData.location }}</p>
        </div>
      </div>
    </header>

    <section id="about" class="p-8 md:p-12 bg-[#16241f] border-b border-[#b88c4c]/20">
      <h2 class="text-3xl font-black uppercase mb-4">About</h2>
      <p class="text-sm text-gray-400 max-w-2xl leading-relaxed">{{ devData.fullBio }}</p>
    </section>

    <section id="experience" class="p-8 md:p-12 bg-[#1c2c26] border-b border-[#b88c4c]/20">
      <h2 class="text-3xl font-black uppercase mb-8">Experience</h2>
      <div class="space-y-6">
        <div v-for="(exp, i) in experiences" :key="i" class="pl-4 border-l-2 border-[#b88c4c]/30">
          <h3 class="font-bold text-[#e4e4e0]">
            {{ exp.role }} <span class="text-gray-400 font-light">@ {{ exp.company }}</span>
          </h3>
          <span class="text-xs text-[#b88c4c]">{{ exp.period }}</span>
          <p class="text-sm text-gray-400 mt-2">{{ exp.description }}</p>
        </div>
      </div>
    </section>

    <section id="works" class="p-8 md:p-12 bg-[#16241f] border-b border-[#b88c4c]/20">
      <h2 class="text-3xl font-black uppercase mb-8">Works</h2>
      <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
        <a
          v-for="(project, i) in projects"
          :key="i"
          :href="project.liveUrl"
          target="_blank"
          class="bg-[#1c2c26] border border-[#b88c4c]/20 p-4 hover:border-[#b88c4c] transition"
        >
          <h3 class="font-bold text-[#b88c4c] uppercase text-sm mb-2">{{ project.title }}</h3>
          <p class="text-xs text-gray-400">{{ project.description }}</p>
        </a>
      </div>
    </section>

    <footer id="contact" class="p-8 md:p-12 bg-[#1c2c26] text-center border-t border-[#b88c4c]/20">
      <h2 class="text-3xl font-black uppercase mb-4">Get In Touch</h2>
      <a
        :href="'mailto:' + devData.email"
        class="inline-block px-6 py-2 border border-[#b88c4c] text-[#b88c4c] hover:bg-[#b88c4c] hover:text-black transition text-sm font-bold uppercase"
      >
        Email Me
      </a>
      <p class="text-xs text-gray-500 mt-8">© 2026 {{ devData.name }}. Built with Vue 3.</p>
    </footer>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const devData = ref({
  name: 'GANZA LORENZO',
  role: 'Frontend Developer',
  bio: 'Building scalable web experiences with Vue 3 & modern tools.',
  fullBio:
    'Passionate frontend engineer from Kigali, Rwanda with expertise in Vue 3, JavaScript, and responsive design. I craft beautiful, performant web applications and love solving complex problems.',

  photo: './me.JPG',

  website: 'tourmyrwanda.vercel.app',
  location: 'Kigali, Rwanda',
  email: 'ganzalorenzo@outlook.com'
})

const experiences = ref([
  {
    role: 'Frontend Engineer',
    company: 'SOS TECHNICAL SCHOOL',
    period: '2025 — Present',
    description: 'Refactored Vue 3 apps, optimized hydration, built multi-tenant pipelines.'
  },
  {
    role: 'UI/UX Designer',
    company: 'SOS TECHNICAL SCHOOL',
    period: '2020 — 2021',
    description: 'Built responsive components, integrated APIs with async JavaScript.'
  }
])

const projects = ref([
  {
    title: 'Smart Commute Rwanda',
    description: 'Real-time bus tracking with offline SMS/USSD support.',
    liveUrl: '#'
  },
  {
    title: 'Web Dev Portfolio',
    description: 'Semantic, responsive web experiences with Tailwind.',
    liveUrl: '#'
  },
  {
    title: 'Vue.js Systems',
    description: 'Scalable apps with Composition API and reusable composables.',
    liveUrl: '#'
  }
])
</script>

<style>
html {
  scroll-behavior: smooth;
}
</style>
<template>
  <div class="min-h-screen bg-[#1c2c26] text-[#e4e4e0] font-sans">
    <header class="h-screen flex flex-col justify-between p-8 md:p-12 border-b border-[#b88c4c]/20">
      <div>
        <h2 class="text-lg font-bold uppercase">{{ devData.name }}</h2>
        <p class="text-xs text-[#b88c4c] uppercase mt-1">{{ devData.role }}</p>
      </div>
      <h1 class="text-6xl md:text-7xl font-black uppercase leading-tight">Portfolio.</h1>
      <div class="flex justify-between items-end">
        <div class="text-xs text-gray-400">
          <p>{{ devData.website }}</p>
          <p class="text-[#b88c4c] mt-1">{{ devData.location }}</p>
        </div>
      </div>
    </header>

    <section id="experience" class="p-8 md:p-12 bg-[#16241f] border-b border-[#b88c4c]/20">
      <h2 class="text-4xl font-black uppercase mb-8">Experience</h2>
      <div class="space-y-6">
        <div v-for="(exp, i) in experiences" :key="i" class="pl-4 border-l-2 border-[#b88c4c]/30">
          <div class="flex justify-between items-start mb-2">
            <h3 class="font-bold text-[#e4e4e0]">{{ exp.role }} <span class="text-gray-400 font-light">@ {{ exp.company }}</span></h3>
            <span class="text-xs text-[#b88c4c]">{{ exp.period }}</span>
          </div>
          <p class="text-sm text-gray-400 mb-2">{{ exp.description }}</p>
          <div class="flex gap-2 flex-wrap">
            <span v-for="tag in exp.tags" :key="tag" class="text-xs bg-[#1c2c26] text-gray-300 px-2 py-1">{{ tag }}</span>
          </div>
        </div>
      </div>
    </section>

    <section id="works" class="p-8 md:p-12 bg-[#1c2c26] border-b border-[#b88c4c]/20">
      <h2 class="text-4xl font-black uppercase mb-8">Works</h2>
      <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
        <a v-for="(project, i) in projects" :key="i" :href="project.liveUrl" target="_blank" class="bg-[#16241f] border border-[#b88c4c]/20 p-4 hover:border-[#b88c4c] transition">
          <h3 class="font-bold text-[#b88c4c] uppercase text-sm mb-1">{{ project.title }}</h3>
          <p class="text-xs text-gray-400 mb-3">{{ project.description }}</p>
          <div class="flex gap-1 flex-wrap">
            <span v-for="tool in project.tools" :key="tool" class="text-[10px] bg-[#0f1915] text-[#b88c4c] px-1.5 py-0.5">{{ tool }}</span>
          </div>
        </a>
      </div>
    </section>

    <footer id="contact" class="p-8 md:p-12 bg-[#16241f] text-center">
      <h2 class="text-3xl font-black uppercase mb-4">Get In Touch</h2>
      <p class="text-gray-400 mb-6 text-sm">Open to exciting frontend roles</p>
      <a :href="'mailto:' + devData.email" class="inline-block px-6 py-2 border border-[#b88c4c] text-[#b88c4c] hover:bg-[#b88c4c] hover:text-black transition text-sm font-bold uppercase">
        Email Me
      </a>
      <p class="text-xs text-gray-500 mt-8">© 2026 {{ devData.name }}. Built with Vue 3 & Tailwind.</p>
    </footer>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const devData = ref({
  name: 'GANZA LORENZO',
  role: 'Frontend Developer',
  website: 'tourmyrwanda.vercel.app',
  location: 'Kigali, Rwanda',
  email: 'ganzalorenzo@outlook.com'
})

const experiences = ref([
  {
    role: 'Frontend Engineer',
    company: 'SOS TECHNICAL SCHOOL',
    period: '2025 — Present',
    description: 'Refactored Vue 3 apps, optimized hydration, built multi-tenant pipelines.',
    tags: ['Vue 3', 'JavaScript', 'Tailwind CSS']
  },
  {
    role: 'UI/UX Designer',
    company: 'SOS TECHNICAL SCHOOL',
    period: '2020 — 2021',
    description: 'Built responsive components, integrated APIs with async JavaScript.',
    tags: ['JavaScript', 'HTML5', 'Figma']
  }
])

const projects = ref([
  {
    title: 'Smart Commute Rwanda',
    description: 'Real-time bus tracking with offline SMS/USSD support.',
    tools: ['Vue 3', 'Tailwind', 'C++'],
    liveUrl: '#'
  },
  {
    title: 'Web Dev Portfolio',
    description: 'Semantic, responsive web experiences with Tailwind.',
    tools: ['JavaScript', 'Tailwind', 'HTML5'],
    liveUrl: '#'
  },
  {
    title: 'Vue.js Systems',
    description: 'Scalable apps with Composition API and reusable composables.',
    tools: ['Vue 3', 'Vite', 'Composables'],
    liveUrl: '#'
  }
])
</script>

<style>
html { scroll-behavior: smooth; }
</style>
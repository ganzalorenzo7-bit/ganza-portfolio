<template>
  <div class="min-h-screen bg-[#1c2c26] text-[#e4e4e0] font-sans antialiased selection:bg-[#b88c4c] selection:text-black">
    
    <header class="relative grid grid-cols-1 md:grid-cols-12 min-h-screen border-b border-[#b88c4c]/20">
      <div class="md:col-span-4 p-8 lg:p-12 flex flex-col justify-between border-r border-[#b88c4c]/20 bg-[#16241f]">
        <div>
          <h2 class="text-xl font-bold tracking-widest text-[#e4e4e0] uppercase leading-none">{{ devData.name }}</h2>
          <p class="text-xs tracking-wider text-[#b88c4c] uppercase mt-1">{{ devData.role }}</p>
        </div>
        
        <div class="my-12 relative">
          <h1 class="text-7xl lg:text-8xl font-black tracking-tighter text-[#e4e4e0] uppercase leading-[0.85]">
            PORT<br/>FOLIO.
          </h1>
          <div class="mt-8 flex flex-col gap-1.5 w-24 opacity-60">
            <div v-for="n in 6" :key="n" class="h-[3px] bg-[#b88c4c] transform -skew-x-12"></div>
          </div>
        </div>

        <div class="flex items-end justify-between">
          <div class="text-xs text-gray-400 font-mono">
            <p>{{ devData.website }}</p>
            <p class="mt-1 text-[#b88c4c]/100">{{ devData.location }}</p>
          </div>
          <div class="w-12 h-12 border border-[#b88c4c]/30 p-1 flex flex-wrap gap-1 opacity-40">
            <div v-for="i in 4" :key="i" class="w-[20px] h-[20px] border border-[#b88c4c]/50"></div>
          </div>
        </div>
      </div>

      <div class="md:col-span-8 relative flex flex-col justify-between p-8 lg:p-12 overflow-hidden bg-gradient-to-br from-[#1c2c26] to-[#131f1b]">
        <div class="absolute top-[-50px] right-20 w-48 h-48 border border-[#b88c4c]/20 rounded-full pointer-events-none"></div>
        
        <div class="flex justify-between items-start z-10">
          <nav class="flex gap-8 text-xs font-bold tracking-widest uppercase text-gray-400">
            <a href="#experience" class="hover:text-[#b88c4c] transition-colors">Experience</a>
            <a href="#works" class="hover:text-[#b88c4c] transition-colors">Selected Works</a>
            <a href="#contact" class="hover:text-[#b88c4c] transition-colors">Contact</a>
          </nav>
        </div>

        <div class="my-auto max-w-xl grid grid-cols-1 md:grid-cols-12 gap-8 items-center z-10">
          <div class="md:col-span-6 relative aspect-[3/4] bg-neutral-900 border border-[#b88c4c]/30 overflow-hidden group">
            <img 
              :src="devData.avatarUrl" 
              alt="Developer Profile Image" 
              class="w-full h-full object-cover grayscale contrast-125 brightness-90 transition duration-500 group-hover:scale-105"
            />
            <div class="absolute inset-0 bg-gradient-to-t from-black/50 to-transparent"></div>
          </div>
          <div class="md:col-span-6">
            <h3 class="text-2xl font-bold text-[#b88c4c] uppercase tracking-tight mb-4">Statement</h3>
            <p class="text-sm text-gray-300 leading-relaxed font-light">
              {{ devData.statement }}
            </p>
          </div>
        </div>
      </div>
    </header>

    <section id="experience" class="grid grid-cols-1 md:grid-cols-12 border-b border-[#b88c4c]/20">
      <div class="md:col-span-4 p-8 lg:p-12 bg-[#16241f] md:border-r border-[#b88c4c]/20">
        <h2 class="text-5xl font-black text-[#e4e4e0] uppercase tracking-tighter sticky top-12 leading-none">
          Working<br/>Experiences
        </h2>
        <div class="mt-8 relative w-32 h-32 border border-[#b88c4c]/10 rounded-full hidden md:block">
          <div class="absolute -bottom-4 right-4 w-12 h-12 border-t border-l border-[#b88c4c]/30"></div>
        </div>
      </div>

      <div class="md:col-span-8 p-8 lg:p-12 space-y-12 bg-[#1c2c26]">
        <div 
          v-for="(exp, index) in experiences" 
          :key="index" 
          class="group relative pl-8 border-l-2 border-[#b88c4c]/30 hover:border-[#b88c4c] transition-colors pb-4"
        >
          <div class="absolute -left-[7px] top-1.5 w-3 h-3 bg-[#1c2c26] border-2 border-[#b88c4c] rounded-full group-hover:bg-[#b88c4c] transition-colors"></div>
          
          <div class="flex flex-col sm:flex-row sm:items-center justify-between mb-2">
            <h3 class="text-xl font-bold text-[#e4e4e0] group-hover:text-[#b88c4c] transition-colors uppercase tracking-tight">
              {{ exp.role }} <span class="text-gray-400 font-light">@ {{ exp.company }}</span>
            </h3>
            <span class="text-sm font-mono text-[#b88c4c] font-bold mt-1 sm:mt-0">{{ exp.period }}</span>
          </div>
          <p class="text-sm text-gray-400 font-light max-w-2xl leading-relaxed mb-3">
            {{ exp.description }}
          </p>
          <div class="flex flex-wrap gap-2">
            <span v-for="tech in exp.tags" :key="tech" class="text-[10px] uppercase font-mono tracking-wider bg-[#16241f] text-gray-300 border border-white/5 px-2 py-0.5">
              {{ tech }}
            </span>
          </div>
        </div>
      </div>
    </section>

    <section id="works" class="p-8 lg:p-12 bg-[#16241f] border-b border-[#b88c4c]/20">
      <div class="flex flex-col md:flex-row justify-between items-baseline mb-12 border-b border-[#b88c4c]/20 pb-6">
        <h2 class="text-5xl font-black text-[#e4e4e0] uppercase tracking-tighter">My Latest Works</h2>
        <p class="text-xs font-mono text-[#b88c4c] mt-2 md:mt-0">SELECTED ENGINEERING ARTIFACTS / VUE & JS</p>
      </div>

      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
        <div 
          v-for="(project, index) in projects" 
          :key="index" 
          class="flex flex-col bg-[#1c2c26] border border-[#b88c4c]/10 hover:border-[#b88c4c]/40 transition duration-300 group"
        >
          <div class="relative aspect-video bg-neutral-900 border-b border-[#b88c4c]/10 overflow-hidden">
            <img 
              :src="project.imageUrl" 
              :alt="project.title" 
              class="w-full h-full object-cover grayscale contrast-115 group-hover:scale-102 group-hover:grayscale-0 transition duration-500"
            />
            <div class="absolute bottom-2 right-2 flex gap-1 opacity-0 group-hover:opacity-100 transition-opacity duration-300">
              <div v-for="n in 3" :key="n" class="w-1 h-4 bg-[#b88c4c] transform -skew-x-12"></div>
            </div>
          </div>

          <div class="p-6 flex-1 flex flex-col justify-between">
            <div>
              <div class="flex justify-between items-start mb-2">
                <h3 class="text-lg font-bold text-[#e4e4e0] uppercase tracking-tight group-hover:text-[#b88c4c] transition-colors">
                  {{ project.title }}
                </h3>
                <span class="text-xs font-mono text-gray-500">0{{ index + 1 }}</span>
              </div>
              <p class="text-xs text-gray-400 font-light leading-relaxed mb-4">
                {{ project.description }}
              </p>
            </div>

            <div>
              <div class="flex flex-wrap gap-1.5 mb-4">
                <span v-for="tag in project.tools" :key="tag" class="text-[10px] uppercase font-mono tracking-wider bg-[#16241f] text-[#b88c4c] px-2 py-0.5">
                  {{ tag }}
                </span>
              </div>
              <div class="flex gap-4 border-t border-[#b88c4c]/10 pt-3">
                <a :href="project.liveUrl" target="_blank" class="text-xs font-bold uppercase tracking-widest text-[#e4e4e0] hover:text-[#b88c4c] transition-colors flex items-center gap-1">
                  Live Site ↗
                </a>
                <a :href="project.repoUrl" target="_blank" class="text-xs font-bold uppercase tracking-widest text-gray-400 hover:text-[#b88c4c] transition-colors">
                  Codebase
                </a>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <footer id="contact" class="grid grid-cols-1 md:grid-cols-12 min-h-[60vh] bg-[#16241f]">
      <div class="md:col-span-4 p-8 lg:p-12 flex flex-col justify-between border-r border-[#b88c4c]/20 relative overflow-hidden bg-[#121d19]">
        <div class="absolute -bottom-10 -left-10 w-40 h-40 border border-[#b88c4c]/10 rounded-full"></div>
        
        <h2 class="text-7xl font-black text-white/5 uppercase tracking-tighter select-none leading-none">
          SAY<br/>HELLO.
        </h2>
        
        <div class="z-10">
          <p class="text-xs tracking-widest text-[#b88c4c] uppercase font-bold mb-1">Current Availability</p>
          <p class="text-sm text-gray-400 font-light font-mono">Open to high-impact engineering roles.</p>
        </div>
      </div>

      <div class="md:col-span-8 p-8 lg:p-12 flex flex-col justify-between bg-[#1c2c26] relative">
        <div class="max-w-xl">
          <h2 class="text-5xl font-black text-[#e4e4e0] uppercase tracking-tighter mb-4 leading-none">Thank You</h2>
          <p class="text-sm text-gray-300 font-light leading-relaxed mb-8">
            Looking for a clean, structural frontend application layout built correctly from architectural blueprints? Let's talk strategy.
          </p>

          <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
            <a :href="'mailto:' + devData.email" class="p-4 border border-[#b88c4c]/20 bg-[#16241f] text-center hover:border-[#b88c4c] transition-colors group">
              <span class="block text-[10px] uppercase font-mono tracking-widest text-gray-400 group-hover:text-[#b88c4c]">Direct Email</span>
              <span class="text-sm font-bold text-[#e4e4e0]">{{ devData.email }}</span>
            </a>
            <div class="p-4 border border-[#b88c4c]/20 bg-[#16241f] flex justify-around items-center">
              <a v-for="social in devData.socials" :key="social.name" :href="social.url" target="_blank" class="text-xs font-bold uppercase tracking-widest text-gray-400 hover:text-[#b88c4c] transition-colors">
                {{ social.name }}
              </a>
            </div>
          </div>
        </div>

        <div class="flex flex-col sm:flex-row justify-between items-start sm:items-center text-xs font-mono text-gray-500 mt-12 pt-6 border-t border-[#b88c4c]/10">
          <p>© 2026 {{ devData.name }}. Built using Vue 3 & Tailwind CSS.</p>
          <div class="flex gap-1 mt-2 sm:mt-0">
            <div v-for="n in 8" :key="n" class="w-1.5 h-1.5 bg-[#b88c4c]/30 transform -skew-x-12"></div>
          </div>
        </div>
      </div>
    </footer>

  </div>
</template>

<script setup>
import { ref } from 'vue'

const devData = ref({
  name: 'GANZA LORENZO ANYIEGA',
  role: 'INTERMEDIATE SOFTWARE DEVELOPER',
  website: 'tourmyrwanda.vercel.app',
  location: 'Kigali, Rwanda',
  avatarUrl: './public/me.JPG', 
  email: 'ganzalorenzo@outlook.com',
  statement : 'Specializing in developing clean codes, shaping app layout layers, and system architecture. I build optimized client-side systems using tailored responsive styles.',
  socials: [
    { name: 'GitHub', url: 'ganzalorenzo7-bit' },
    { name: 'Instagram', url: 'loganzaganzalo' },
  ]
})

const experiences = ref([
  {
    role: 'Frontend Engineer',
    company: 'SOS TECHNICAL SCHOOL',
    period: '2025 — PRESENT',
    description: 'Refactored aging single-page app views into high-performance Vue 3 compositional interfaces. Reduced overall hydration delays and customized strict validation patterns for multi-tenant data pipelines.',
    tags: ['Vue', 'Javascript', 'Tailwind CSS', 'Vite']
  },
  {
    role: 'UI/UX Designer',
    company: 'SOS TECHNICAL SCHOOL',
    period: '2020 — 2021',
    description: 'Constructed responsive, dynamic landing elements and single components from static interactive prototypes. Handled API payload connectivity using modern asynchronous Javascript loops.',
    tags: ['JavaScript', 'HTML5', 'Figma']
  }
])

const projects = ref([
  {
    title: 'SMART COMMUTE RWANDA',
    description: 'Smart Commute Rwanda makes bus travel simple and predictable. It gives passengers real-time arrival times to eliminate waiting, plus an offline SMS/USSD feature so people without smartphones can instantly check bus schedules and prices.',
    imageUrl: './public/commute.jpg',
    tools: ['Vue 3', 'Tailwind CSS', 'C++'],
    liveUrl: '#',
    repoUrl: '#'
  },
  {
    title: 'CORE WEB DEVELOPMENT ARTIFACTS',
    description: 'Engineering highly performant, semantic web experiences engineered from scratch. Specialized in breaking down rigid, static designs into responsive, beautiful UI layouts using deep utility tracking with Tailwind CSS and advanced modern JavaScript configurations.',
    imageUrl: 'https://images.unsplash.com/photo-1542831371-29b0f74f9713?auto=format&fit=crop&q=80&w=600',
    tools: ['JavaScript', 'Tailwind CSS', 'HTML5', 'CSS Architecture'],
    liveUrl: '#',
    repoUrl: '#'
  },
  {
    title: 'ADVANCED VUE.JS APPLICATION SPEC',
    description: 'Architecting scalable client-side systems with Vue 3 and the Composition API. Expert utilization of custom single-file components, reusable composables, declarative reactive state mechanics, and optimized data fetching layers.',
    imageUrl: 'https://images.unsplash.com/photo-1504868584819-f8e8b4b6d7e3?auto=format&fit=crop&q=80&w=600',
    tools: ['Vue 3', 'Composition API', 'Vite', 'Reusables'],
    liveUrl: '#',
    repoUrl: '#'
  }
])
</script>

<style>
html {
  scroll-behavior: smooth;
}
</style>
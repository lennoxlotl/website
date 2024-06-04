<script setup>
import SkillList from '@/components/SkillList.vue'
import ProjectCard from '@/components/ProjectCard.vue'
import { AcademicCapIcon } from '@heroicons/vue/24/solid';
import { createScrollRevealDirective } from 'vue-scroll-reveal';

const programmingLanguages = [
  {
    name: 'Java'
  },
  {
    name: 'Kotlin'
  },
  {
    name: 'Rust'
  },
  {
    name: 'C',
    note: 'Partially'
  },
  {
    name: 'Web Stack',
    note: 'Vue, JS, CSS, HTML'
  }
]

const frameworks = [
  {
    name: 'Kubernetes'
  },
  {
    name: 'Docker'
  },
  {
    name: 'Tauri'
  },
  {
    name: 'Spring Framework'
  },
  {
    name: 'PostgreSQL, MongoDB, MySQL, Redis',
    note: 'Databases'
  }
]

const currentProjects = [
  {
    name: 'Intave',
    description:
      'Minecraft anti-cheat solution for all major server versions, used by large networks such as GommeHD.net!',
    link: 'https://intave.ac',
    preview: 'intave.ac',
    owned: false
  },
  {
    name: 'Rainbowify',
    description:
      'Minecraft Fabric Mod that adds a nice rainbow and blur effect to inventory screens',
    link: 'https://github.com/lennoxlotl/rainbowify',
    preview: 'github.com',
    owned: true
  }
]

const pastProjects = [
  {
    name: 'PlayLegend',
    description: 'Minecraft server providing a unique gameplay experience while staying on the newest minecraft version',
    link: 'https://playlegend.net',
    preview: 'playlegend.net',
    owned: false
  }
]

const vReveal = createScrollRevealDirective({
  delay: 0,
  duration: 700,
  distance: '20px',
  origin: 'top'
})
</script>

<template>
  <div class="load-hidden" v-reveal>
    <p class="text-3xl font-bold">👋 Hi there!</p>
    <p class="pt-2">
      I'm Lennox, an 18 year old full-stack software developer with a diverse skill set currently
      studying in university.
      <br />
      Here's a list of frameworks and languages I am familiar with:
    </p>

    <SkillList class="pt-5" title="🖥️ Programming languages" :content="programmingLanguages"></SkillList>
    <SkillList class="pt-5" title="🔧 Frameworks and tools" :content="frameworks"></SkillList>

    <p class="text-3xl font-bold pt-8">🪄 My projects</p>
    <p class="pt-2">
      These are the most notable projects I am contributing to as a software developer.
      <br />
      You can find more projects on my GitHub page.
    </p>
    <div class="pt-4 grid md:grid-cols-2 gap-4">
      <ProjectCard v-for="project in currentProjects" :name="project.name" :description="project.description"
        :link="project.link" :preview="project.preview" :owned="project.owned">
      </ProjectCard>
    </div>

    <p class="text-3xl font-bold pt-8">📨 Past projects</p>
    <p class="pt-2">These are projects I contributed to in the past or have ended.</p>
    <div class="pt-4 grid md:grid-cols-2 gap-4">
      <ProjectCard v-for="project in pastProjects" :name="project.name" :description="project.description"
        :link="project.link" :preview="project.preview" :owned="project.owned">
      </ProjectCard>
    </div>

    <p class="flex items-center mt-4 text-sm text-zinc-500">Projects notated with <span>
        <AcademicCapIcon class="w-4 mx-1"></AcademicCapIcon>
      </span> are owned by me.
    </p>
  </div>
</template>

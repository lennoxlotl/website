<script setup>
import { createScrollRevealDirective } from 'vue-scroll-reveal'

const vReveal = createScrollRevealDirective({
  delay: 0,
  duration: 700,
  distance: '20px',
  origin: 'bottom'
})
</script>

<template>
  <div class="load-hidden" v-reveal>
    <p class="text-3xl font-bold">📁 File hosting</p>
    <p class="pt-2 font-semibold">🚧 Currently private and experimental</p>
    <p class="pt-2">
      Very simple file hosting with caching powered by Cloudflare. <br />
      The service is entirely open-source under a MIT-license and is available
      <a
        href="https://github.com/lennoxlotl/uploader"
        class="text-gray-400 hover:text-blue-400 transition font-bold"
        >here</a
      >
    </p>
  </div>
</template>

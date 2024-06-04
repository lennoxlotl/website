<script setup>
import HeaderLink from '@/components/HeaderLink.vue'
</script>

<template>
  <div class="flex flex-row items-center pb-4 px-0.5 border-b border-zinc-700">
    <div class="flex flex-row items-center">
      <img src="@/assets/logo.png" class="w-8" />
      <p class="pl-2.5 text-xl font-extrabold geist-mono">lennoxlotl.dev</p>
    </div>

    <div class="flex flex-row ml-auto">
      <HeaderLink to="/" name="Home" />
      <HeaderLink class="ml-4" to="/contact" name="Contact" />
    </div>
  </div>
</template>

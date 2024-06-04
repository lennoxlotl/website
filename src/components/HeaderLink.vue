<script setup>
import { useRoute, useRouter } from 'vue-router'

const props = defineProps({
  to: String,
  name: String
})

const route = useRoute()
const router = useRouter()

function isCurrent() {
  return route.path == props.to
}

function goToRoute() {
  router.push({ path: props.to })
}
</script>

<template>
  <div>
    <button
      :href="to"
      class="geist-mono transition font-semibold"
      :class="{ 'text-blue-400': isCurrent(), 'hover:text-white text-zinc-300': !isCurrent() }"
      v-on:click="goToRoute"
    >
      {{ name }}
    </button>
  </div>
</template>

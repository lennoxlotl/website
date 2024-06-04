<script setup>
defineProps({
  title: String,
  content: Object
})
</script>

<template>
  <div>
    <p class="text-xl font-bold">{{ title }}</p>
    <ul class="list-disc list-inside pt-1">
      <li v-for="item in content">
        <span>{{ item.name }}</span>
        <span v-if="item.note" class="pl-1 text-zinc-400 text-xs font-bold">({{ item.note }})</span>
      </li>
    </ul>
  </div>
</template>

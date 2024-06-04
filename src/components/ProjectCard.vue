<script setup>
import { AcademicCapIcon, LinkIcon } from '@heroicons/vue/24/solid'

const props = defineProps({
    name: String,
    description: String,
    link: String,
    preview: String,
    owned: Boolean
})

function navigateTo() {
    window.location = props.link
}
</script>

<template>
    <div class="h-full">
        <button
            class="shadow-xl bg-zinc-900 hover:bg-zinc-800/[0.3] border border-zinc-400/[0.15] rounded-2xl px-3.5 py-4 text-left transition flex flex-col h-full w-full"
            v-on:click="navigateTo">
            <p class="font-bold flex">
                <AcademicCapIcon v-if="owned" class="w-4 mr-1 text-zinc-400"></AcademicCapIcon>
                {{ name }}
            </p>
            <p class="pt-1.5 text-sm text-zinc-400">{{ description }}</p>
            <p class="text-blue-400 pt-1 text-sm flex items-center mt-auto">
                <span>
                    <LinkIcon class="w-4 mr-1.5"></LinkIcon>
                </span>
                {{ preview }}
            </p>
        </button>
    </div>
</template>

<script setup>
import { AtSymbolIcon, ChatBubbleBottomCenterIcon, ClipboardDocumentIcon, EnvelopeIcon } from '@heroicons/vue/24/solid';
import { ref } from 'vue';
import { createScrollRevealDirective } from 'vue-scroll-reveal';

const copyButtonText = ref('Click to copy the public key');

const contactInfo = [
  {
    name: 'Mail',
    value: 'admin@lennoxlotl.dev',
    link: 'mailto:admin@lennoxlotl.dev',
    icon: EnvelopeIcon
  },
  {
    name: 'Discord',
    value: '@lennoxlotl',
    link: 'https://discord.com/users/300229572350312448',
    icon: AtSymbolIcon
  },
  {
    name: 'Telegram',
    value: '@lennoxlotl',
    link: 'https://t.me/lennoxlotl',
    icon: ChatBubbleBottomCenterIcon
  }
]

const keyInfo = [
  {
    name: 'User-ID',
    value: 'Lennox Schneider <admin@lennoxlotl.dev>'
  },
  {
    name: 'Type',
    value: 'ECC (Curve25519)'
  },
  {
    name: 'Fingerprint',
    value: 'b1e1114bdafdaf366c7437130944a2b4187015df'
  }
]

const publicKey = `
-----BEGIN PGP PUBLIC KEY BLOCK-----

xjMEZRrM+xYJKwYBBAHaRw8BAQdAzlbulWkOtvPs1zYfJRezyab6YupSnt6d
DGghXqkpgxHNK2FkbWluQGxlbm5veGxvdGwuZGV2IDxhZG1pbkBsZW5ub3hs
b3RsLmRldj7CjAQQFgoAPgWCZRrM+wQLCQcICZAJRKK0GHAV3wMVCAoEFgAC
AQIZAQKbAwIeARYhBLHhEUva/a82bHQ3EwlEorQYcBXfAAAFXgD9EBpk15D0
GtPjMLYrwb7LjJyAVRnwdJLxp6yqNP+rufMA/jTW0EEmlTJG746jXTO+Bnzl
kWNbiSGfN5EjYj9mvqUDzjgEZRrM+xIKKwYBBAGXVQEFAQEHQEi+9o9AQLnT
jXW7sQtUvaARHMEcJv+o2Fl6Zi+UniVGAwEIB8J4BBgWCAAqBYJlGsz7CZAJ
RKK0GHAV3wKbDBYhBLHhEUva/a82bHQ3EwlEorQYcBXfAADQWwEA68iKzKI/
Mkc/9VW0ABLcjAPJ7iTFfZlXyYlvsb/d+uwBALz7qs80khio5M02D+1SZTSQ
oUj9R/j1YJGBGNgJNroD
=1VUJ
-----END PGP PUBLIC KEY BLOCK-----
`;

const delay = ms => new Promise(res => setTimeout(res, ms));

async function copyPublicKey() {
  copyButtonText.value = "Copied!";
  navigator.clipboard.writeText(publicKey);
  await delay(1000);
  copyButtonText.value = "Click to copy the public key"
}

const vReveal = createScrollRevealDirective({
  delay: 0,
  duration: 700,
  distance: '20px',
})
</script>

<template>
  <div class="load-hidden" v-reveal>
    <p class="text-3xl font-bold">✉️ Contact me</p>
    <p class="pt-2">
      Need anything? Contact me through one of the listed methods below.
    </p>
    <div class="flex flex-col divide-y divide-zinc-800 pt-2">
      <p v-for="contact in contactInfo" class="flex flex-row text-sm py-2 items-center">
        <span class="text-zinc-500 flex gap-1.5">
          <component :is="contact.icon" class="w-4"></component>
          <p class="font-semibold">{{ contact.name }}</p>
        </span>
        <a class="font-bold text-blue-400 hover:text-blue-500 ml-auto transition overflow-x-auto geist-mono"
          :href="contact.link">{{ contact.value
          }}</a>
      </p>
    </div>
    <p class="text-2xl font-bold pt-6">🔒 Secure</p>
    <p class="pt-2">Sensitive data shall be encrypted with the PGP key provided below for your own security </p>
    <p class="pt-4 font-bold text-xl">Key Information</p>
    <div class="flex flex-col divide-y divide-zinc-800 pt-2">
      <p v-for="info in keyInfo" class="flex flex-row text-sm py-2 items-center">
        <span class="text-zinc-500 flex gap-1.5">
          <component :is="info.icon" class="w-4"></component>
          <p class="text-nowrap font-semibold">{{ info.name }}</p>
        </span>
      <p class="text-nowrap font-bold text-zinc-300 ml-auto transition overflow-x-auto geist-mono">{{
        info.value
      }}</p>
      </p>
    </div>
    <p class="pt-4 font-bold text-xl">Public key</p>
    <button class="pt-4 text-sm text-zinc-500 flex" v-on:click="copyPublicKey">
      <ClipboardDocumentIcon class="w-4 mr-1"></ClipboardDocumentIcon>
      {{ copyButtonText }}
    </button>
  </div>
</template>

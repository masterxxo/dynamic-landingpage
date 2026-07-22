<template>
  <footer class="w-screen bg-violet-300 py-4 text-black">
    <div class="container mx-auto flex flex-com items-center justify-between gap-4 px-4 md:flex-row">
      <p class="text-center text-sm md:text-left">
        &copy; Made with &hearts; by <a href="https://rogson.dev" target="_blank" rel="noopener noreferrer" class="underline text-black transition-colors duration-500 ease-in-out hover:text-white">Rogson.dev</a>
      </p>
      <div class="flex justify-center gap-4 md:justify-start">
        <a
          v-for="(link) in socialLinks"
          :key="link.href"
          :href="link.href"
          target="_blank"
          rel="noopener noreferrer"
          class="text-black transition-colors duration-500 ease-in-out hover:text-white"
        >
          <i class="typcn" :class="link.icon"></i>
        </a>
      </div>
      <a href="#privacy-policy" class="text-center text-sm hover:underline md:text-right">Privacy Policy</a>
    </div>
  </footer>
</template>
<script lang="ts" setup>
const socialLinks = [
  { href: 'https://x.com/rogson_dev', icon: 'typcn-social-twitter' },
  { href: 'https://github.com/masterxxo', icon: 'typcn-social-github'},
  { href: 'https://www.linkedin.com/in/mateusz-rog/', icon: 'typcn-social-linkedin' },
  { href: 'https://www.instagram.com/mateusz.rog.pl/', icon: 'typcn-social-instagram'}
]
</script>
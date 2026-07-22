<script lang="ts" setup>
import HeroSection from './components/HeroSection.vue';
import AboutSection from './components/AboutSection.vue';
import NavigationBar from './components/NavigationBar.vue';
</script>

<template>
  <main class="relative min-h-screen w-screen overflow-x-hidden">
    <NavigationBar />
    <HeroSection />
    <AboutSection />
  </main>
</template>

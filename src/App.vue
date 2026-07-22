<script lang="ts" setup>
import HeroSection from './components/HeroSection.vue';
import AboutSection from './components/AboutSection.vue';
import NavigationBar from './components/NavigationBar.vue';
import FeaturesSection from './components/FeaturesSection.vue';
import StorySection from './components/StorySection.vue';
</script>

<template>
  <main class="relative min-h-screen w-screen overflow-x-hidden">
    <NavigationBar />
    <HeroSection />
    <AboutSection />
    <FeaturesSection />
    <StorySection />
  </main>
</template>

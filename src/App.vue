<script lang="ts" setup>
import HeroSection from './components/HeroSection.vue';
import AboutSection from './components/AboutSection.vue';
import NavigationBar from './components/NavigationBar.vue';
import FeaturesSection from './components/FeaturesSection.vue';
import StorySection from './components/StorySection.vue';
import ContactSection from './components/ContactSection.vue';
import FooterSection from './components/FooterSection.vue';
</script>

<template>
  <main class="relative min-h-screen w-screen overflow-x-hidden overflow-y-hidden">
    <NavigationBar />
    <HeroSection />
    <AboutSection />
    <FeaturesSection />
    <StorySection />
    <ContactSection />
    <FooterSection />
  </main>
</template>

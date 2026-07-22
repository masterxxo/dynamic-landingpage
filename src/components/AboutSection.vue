<template>
  <div
    id="about"
    class="min-h-screen w-screen"
  >
    <div class="relative mb-8 mt-36 flex flex-col items-center gap-5">
      <h2 class="font-general text-sm uppercase md:text-[10px]">
        Welcome to Zentry
      </h2>
      <AnimatedTitle title="Disc<b>o</b>ver the world's <br /> l<b>a</b>rgest shared adventure" container-class="mt-5 text-black! text-center" />
      <div class="about-subtext">
        <p>The Game of Games begin - your life, now an epic MMORPG</p>
        <p>Zentry unites every player from countless games and platforms</p>
      </div>
    </div>
    <div class="h-dvh w-screen" id="clip">
      <div class="mask-clip-path about-image">
        <img src="/img/about.webp" alt="Background" class="absolute left-0 top-0 size-full object-cover"  />
      </div>
    </div>
  </div>
</template>

<script lang="ts" setup>
import { onMounted } from 'vue';
import AnimatedTitle from './AnimatedTitle.vue';
import gsap from 'gsap';
import { ScrollTrigger } from 'gsap/all';

gsap.registerPlugin(ScrollTrigger);

const animateBackgroundImage = () => {
  const clipAnimation = gsap.timeline({
    scrollTrigger: {
      trigger: '#clip',
      start: 'center center',
      end: '+=800 center',
      scrub: 0.5,
      pin: true,
      pinSpacing: true,
    }
  });

  clipAnimation.to('.mask-clip-path', {
    width: '100vw',
    height: '100vh',
    borderRadius: 0,
  })
}

onMounted(() => {
  animateBackgroundImage();
})
</script>
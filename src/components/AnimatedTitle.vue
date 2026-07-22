<template>
  <div
    ref="containerRef"
    id="title-container"
    class="animated-title"
    :class="containerClass"
  >
    <div
      v-for="(line, index) in titleLines"
      :key="index"
      class="flex-center max-w-full flex-wrap gap-2 px-10 md:gap-3"
    >
      <span
        v-for="(word, i) in lineWords(line)"
        :key="i"
        class="animated-word special-font"
        v-html="word"
      ></span>
    </div>
  </div>
</template>

<script setup lang="ts">
import { computed, useTemplateRef, onMounted } from 'vue';
import gsap from 'gsap';

const props = defineProps({
  title: String,
  containerClass: String,
});

const containerRef = useTemplateRef('containerRef');

const titleLines = computed(() => {
  return props.title?.split('<br />');
});

const lineWords = (line: string) => {
  return line.split(' ');
}

const animateTitle = () => {
  gsap.context(() => {
    const titleAnimation = gsap.timeline({
      scrollTrigger: {
        trigger: containerRef.value,
        start: '100 bottom',
        end: 'center bottom',
        toggleActions: 'play none none reverse'
      }
    })

    titleAnimation.to('.animated-word', {
      opacity: 1,
      transform: 'translate3d(0,0,0) rotateY(0deg) rotateX(0deg)',
      ease: 'power2.inOut',
      stagger: 0.02,
    })
  }, containerRef.value as HTMLDivElement)
}

onMounted(() => {
  animateTitle();
});
</script>
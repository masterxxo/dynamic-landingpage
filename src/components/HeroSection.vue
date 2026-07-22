<template>
  <div class="relative h-dvh w-screen overflow-x-hidden">
    <div v-if="isLoading" class="flex-center absolute z-100 h-dvh w-screen overflow-hidden bg-violet-50">
      <div class="three-body">
        <div class="three-body__dot"></div>
        <div class="three-body__dot"></div>
        <div class="three-body__dot"></div>
      </div>
    </div>
    <div id="video-frame" class="relative z-10 h-dvh w-creen overflow-hidden rounded-lg bg-blue-75">
      <div>
        <div class="mask-clip-path absolute-center absolute z-50 size-64 cursor-pointer rounded-lg overflow-hidden">
          <div
            @click="handleMiniVideoClick"
            class="origin-center scale-50 opacity-0 transition-all duration-500 ease-in hover:scale-100 hover:opacity-100"
          >
            <video
              ref="nextVideoRef"
              :src="getVideoSrc(upcomingVideoIndex)"
              loop
              muted
              id="current-video"
              class="size-64 origin-center scale-150 object-cover object-center"
              @loadeddata="handleVideoLoad"
            />
          </div>
        </div>
        <video
          ref=""
          :src="getVideoSrc(currentIndex)"
          autoplay
          loop
          muted
          id="next-video"
          class="absolute-center invisible absolute z-20 size-64 object-cover object-center"
          @loadeddata="handleVideoLoad"
        />
        <video
          :src="getVideoSrc((currentIndex === totalVideos - 1) ? 1 : currentIndex)"
          autoplay
          loop
          muted
          id="video-frame"
          class="absolute left-0 top-0 size-full object-cover object-center"
          @loadeddata="handleVideoLoad"
        />
      </div>
      <h1 class="special-font hero-heading absolute bottom-5 right-5 z-40 text-blue-75">
        G<b>a</b>ming
      </h1>
      <div class="absolute left-0 top-0 z-40 size-full">
        <div class="mt-24 px-5 sm:px-10">
          <h2 class="special-font hero-heading text-blue-100">Redefi<b>n</b>e</h2>
          <p class="mb-5 max-w-64 font-robert-regular text-blue-100">
            Enter the Metagame Layer <br />
            Unleash the Play Economy
          </p>
          <MainButton
            id="watch-trailer"
            title="Watch trailer"
            left-icon="typcn-location-arrow"
            container-class="bg-yellow-300 flex-center gap-1 hover:bg-blue-50 duration-500 ease-in-out transition-all hover:scale-105"
          />
        </div>
      </div>
    </div>
      <h2 class="special-font hero-heading absolute bottom-5 right-5 text-black">
        G<b>a</b>ming
      </h2>
  </div>
</template>

<script lang="ts" setup>
import { ref, type Ref, useTemplateRef, computed, onMounted, watch } from 'vue';
import gsap from 'gsap';
import { ScrollTrigger } from 'gsap/all';
import MainButton from './MainButton.vue';

gsap.registerPlugin(ScrollTrigger);

const currentIndex: Ref<number> = ref(1);
const hasClicked: Ref<boolean> = ref(false);
const loadedVideos: Ref<number> = ref(0);

let ctx: gsap.Context;
const totalVideos = 4;
const nextVideoRef = useTemplateRef('nextVideoRef');

const upcomingVideoIndex = computed(() => {
  return (currentIndex.value % totalVideos) + 1}
);

const isLoading = computed(() => {
  return loadedVideos.value !== totalVideos -1;
})

const handleVideoLoad = () => {
  loadedVideos.value = loadedVideos.value + 1;
  if(loadedVideos.value > totalVideos - 1) {
    loadedVideos.value = totalVideos - 1;
  }
}

const handleMiniVideoClick = () => {
  hasClicked.value = true;
  currentIndex.value = upcomingVideoIndex.value;
}

const getVideoSrc = (index: number) => `videos/hero-${index}.mp4`;

const animateVideoScrollChange = () => {
    gsap.set('#video-frame', {
    clipPath: 'polygon(14% 0%, 72% 0%, 90% 90%, 0% 100%)',
    borderRadius: '0 0 40% 10%',
  });

  gsap.from('#video-frame', {
    clipPath: 'polygon(0% 0%, 100% 0%, 100% 100%, 0% 100%)',
    borderRadius: '0 0 0 0',
    ease: 'power1.inOut',
    scrollTrigger: {
      trigger: '#video-frame',
      start: 'center center',
      end: 'bottom center',
      scrub: true,
    }
  })
};

const animateVideoChange = () => {
    gsap.set('#next-video', { visibility: 'visible' });
    gsap.to('#next-video', {
      transformOrigin: 'center center',
      scale: 1,
      width: '100%',
      height: '100%',
      duration: 1,
      ease: "power1.inOut",
      onStart: () => nextVideoRef.value?.play(),
    });
    gsap.from('#current-video', {
      transformOrigin: 'center center',
      scale: 0,
      duration: 1.5,
      ease: "power1.inOut",
    });
}

watch(currentIndex, () => {
  if(hasClicked.value) {
    if(ctx) {
      ctx.revert();
    }
    ctx = gsap.context(animateVideoChange);
  }
})

onMounted(() => {
  animateVideoScrollChange();
});
</script>
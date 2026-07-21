<template>
  <div class="relative h-dvh w-screen overflow-x-hidden">
    <div id="video-frame" class="relative z-10 h-dvh w-creen overflow-hidden rounded-lg bg-blue-75">
      <div>
        <div class="mask-clip-path absolute-center absolute z-50 size-64 cursor-pointer rounded-lg overflow-hidden">
          MiniVideoPlayer
        </div>
      </div>
    </div>
    <!-- <h1 class="text-5xl text-violet-300 font-bold font-circular-web">Welcome to Awwwards</h1> -->
  </div>
</template>

<script lang="ts" setup>
import { ref, type Ref } from 'vue';
const currentIndex: Ref<number> = ref(1);
const hasClicked: Ref<boolean> = ref(false);
const isLoading: Ref<boolean> = ref(true);
const loadedVideos: Ref<number> = ref(0);

const handleMiniVideoClick = () => {

}
</script>
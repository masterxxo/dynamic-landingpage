<template>
  <div class="relative size-full">
    <video
      :src="src"
      loop
      muted
      autoplay
      class="absolute left-0 top-0 size-full object-cover object-center"
    />
    <div class="relative z-10 flex size-full flex-col justify-between p-5 text-blue-50">
      <div>
        <h2 class="bento-title special-font" v-html="title"></h2>
        <p v-if="description" class="mt-3 max-w-64 text-xs md:text-base">
          {{ description }}
        </p>
      </div>
    </div>
  </div>
</template>

<script lang="ts" setup>
const props = defineProps({
  src: String,
  title: String,
  description: String,
});
</script>
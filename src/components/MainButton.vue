<template>
  <button class="group relative z-10 w-fit cursor-pointer overflow-hidden rounded-full bg-violet-50 px-7 py-3 text-black" :class="containerClass">
    <i v-if="leftIcon" class="typcn" :class="leftIcon"></i>
    <span class="relative inline-flex overflow-hidden font-general text-xs uppercase">
      <div>
        {{ title }}
      </div>
    </span>
    <i v-if="rightIcon" class="typcn" :class="rightIcon"></i>
  </button>
</template>

<script lang="ts" setup>
const props = defineProps({
  title: String,
  leftIcon: String,
  rightIcon: String,
  containerClass: String
})
</script>
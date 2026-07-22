<template>
  <div id="contact" class="my-20 min-h-96 w-screen px-10">
    <div class="relative rounded-lg bg-black py-24 text-blue-50 sm:overflow-hidden">
      <div class="absolute -left-20 top-0 hidden h-full w-72 overflow-hidden sm:block lg:left-20 lg:w-96">
        <div class="contact-clip-path-1">
          <img src="/img/contact-1.webp" />
        </div>
        <div class="contact-clip-path-2 lg:translate-y-40 translate-y-60">
          <img src="/img/contact-2.webp" />
        </div>
      </div>
      <div class="absolute -top-40 left-20 w-60 sm:top-1/2 md:left-auto md:right-10 lg:top-20 lg:w-80">
        <div class="absolute md:scale-125">
          <img src="/img/swordman-partial.webp" />
        </div>
        <div class="sword-man-clip-path md:scale-125">
          <img src="/img/swordman.webp" />
        </div>
      </div>
      <div class="flex flex-col items-center text-center">
        <p class="font-general text-[10px] uppercase">Join Zentry</p>
        <p class="special-font mt-10 w-full font-zentry text-5xl leading-[0.9] md:text-[6rem]">
          Let's b<b>u</b>ild the <br /> new era of <br /> g<b>a</b>ming t<b>o</b>gether
        </p>
        <MainButton title="contact us" container-class="mt-10 cursor-pointer hover:bg-yellow-300 duration-500 ease-in-out transition-all hover:scale-105" />
      </div>
    </div>
  </div>
</template>
<script lang="ts" setup>
import MainButton from './MainButton.vue';
</script>
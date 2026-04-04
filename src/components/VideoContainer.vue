<script setup lang="ts">
import videoSrc from '../assets/renovation_video.mp4'
import QuoteButton from './QuoteButton.vue'
</script>

<template>
  <div class="relative">
    <video
      :src="videoSrc"
      autoplay
      loop
      muted
      playsinline
      class="w-full h-full object-cover"
    ></video>
    <div class="absolute inset-0 bg-black/50"></div>
    <div
      class="absolute inset-0 text-white text-2xl font-bold flex items-center justify-center flex-col"
    >
      <h1 class="text-3xl font-bold italic leading-tight md:text-[56px]">
        <span class="text-[#E2722F]">One Stop Renovation</span>
        <span class="block text-white">Contracting Specialist</span>
      </h1>
      <p class="italic leading-relaxed text-white md:text-xl font-normal">
        Our experience guides every build,
        <br />
        and your comfort guides every decision.
      </p>
      <div class="mt-6">
        <QuoteButton />
      </div>
    </div>
  </div>
</template>

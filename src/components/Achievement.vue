<script setup lang="ts">
import ViewMoreButton from './ViewMoreButton.vue'
import AchievementSlider from './AchievementSlider.vue'
</script>

<template>
  <div class="bg-white py-20 md:py-28">
    <div class="max-w-7xl mx-auto">
      <div class="text-center mb-12 font-bold md:text-left">
        <div class="text-3xl leading-tight text-black md:text-4xl lg:text-[42px]">
          Discover Our <br /><span class="italic text-[#E2722F]">Completed Projects</span>
        </div>
        <div
          class="mx-auto mt-4 max-w-full leading-relaxed md:mx-0 flex flex-col md:flex-row justify-between gap-6"
        >
          <div class="font-normal text-black">
            Browse through our latest renovation works and find inspiration for your home.
          </div>
          <ViewMoreButton />
        </div>
      </div>
      <div>
        <AchievementSlider />
      </div>
    </div>
  </div>
</template>

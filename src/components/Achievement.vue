<script setup lang="ts">
import ViewMoreButton from './ViewMoreButton.vue'
import AchievementSlider from './AchievementSlider.vue'
</script>

<template>
  <div class="bg-white py-20 md:py-28 px-4 md:px-6">
    <div class="max-w-7xl mx-auto">
      <div
        class="mb-12 grid gap-6 text-center font-bold md:grid-cols-[minmax(0,1fr)_auto] md:items-end md:text-left"
      >
        <div>
          <div class="text-3xl leading-tight text-black md:text-4xl lg:text-[42px]">
            Discover Our <br /><span class="italic text-[#E2722F]">Completed Projects</span>
          </div>
          <div class="mx-auto mt-4 max-w-md leading-relaxed md:mx-0">
            <div class="font-normal text-black">
              Browse through our latest renovation works and find inspiration for your home.
            </div>
          </div>
        </div>
        <div class="flex justify-center md:justify-end md:self-end">
          <ViewMoreButton />
        </div>
      </div>
      <div>
        <AchievementSlider />
      </div>
    </div>
  </div>
</template>

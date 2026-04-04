<script setup lang="ts">
import TestimonalSlider from './TestimonalSlider.vue'
import WorkingBrand from './WorkingBrand.vue'
</script>

<template>
  <div class="bg-[#ffc247] py-20 md:py-28 text-black relative">
    <div
      class="mx-auto max-w-3xl text-3xl font-bold italic leading-tight text-black md:text-4xl lg:text-[42px] font-medium mb-10"
    >
      Real reviews from clients who upgraded their homes with confidence
    </div>
    <div
      class="pointer-events-none absolute inset-y-0 left-0 z-10 w-16 bg-gradient-to-r from-yellow to-transparent"
    ></div>
    <div
      class="absolute bg-gradient-to-l from-yellow inset-y-0 pointer-events-none right-0 to-transparent w-16 z-10"
    ></div>
    <TestimonalSlider />
    <WorkingBrand />
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'
const workingBrandImages = ref([
  { src: 'bina_group_berhad_brand.png', alt: 'Bina Group Berhad' },
  { src: 'golden_land_brand.png', alt: 'Golden Land Brand' },
  { src: 'haily_group_brand.png', alt: 'Haily Group Brand' },
  { src: 'mah_sing_brand.png', alt: 'Mah Sing Brand' },
  { src: 'newfields_brand.png', alt: 'New Fields Brand' },
  { src: 'pinnacle_brand.svg', alt: 'Pinnacle Brand' }
])
</script>

<template>
  <div class="container mt-10 px-4 md:px-6">
    <div class="mb-4 text-center text-sm font-bold tracking-wide text-black/60">Working With :</div>
    <div class="mx-auto rounded-2xl bg-white px-4 py-6 sm:px-6 md:px-8">
      <div class="grid grid-cols-2 gap-4 md:grid-cols-3 lg:grid-cols-6">
        <div
          v-for="brand in workingBrandImages"
          :key="brand.src"
          class="flex items-center justify-center rounded-lg bg-white p-3"
        >
          <img
            :src="`../src/assets/${brand.src}`"
            :alt="brand.alt"
            width="144"
            height="64"
            class="h-12 w-auto max-w-full object-contain sm:h-14 md:h-16"
            loading="lazy"
          />
        </div>
      </div>
    </div>
  </div>
</template>

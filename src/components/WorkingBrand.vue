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
  <div class="container mt-10">
    <div class="mb-4 text-center text-sm font-bold tracking-wide text-black/60">Working With :</div>
    <div class="bg-white rounded-2xl px-8 py-6">
      <div class="flex justify-center items-center gap-8">
        <img
          v-for="brand in workingBrandImages"
          :key="brand.src"
          :src="`../src/assets/${brand.src}`"
          :alt="brand.alt"
          width="144"
          height="64"
          class="h-16 max-w-36 w-auto object-contain bg-white rounded-lg"
          loading="lazy"
        />
      </div>
    </div>
  </div>
</template>

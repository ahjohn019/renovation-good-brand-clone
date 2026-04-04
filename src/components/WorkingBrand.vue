<script setup lang="ts">
import { ref } from 'vue'

const workingBrandImages = ref([
  {
    src: new URL('../assets/bina_group_berhad_brand.png', import.meta.url).href,
    alt: 'Bina Group Berhad'
  },
  {
    src: new URL('../assets/golden_land_brand.png', import.meta.url).href,
    alt: 'Golden Land Brand'
  },
  {
    src: new URL('../assets/haily_group_brand.png', import.meta.url).href,
    alt: 'Haily Group Brand'
  },
  {
    src: new URL('../assets/mah_sing_brand.png', import.meta.url).href,
    alt: 'Mah Sing Brand'
  },
  {
    src: new URL('../assets/newfields_brand.png', import.meta.url).href,
    alt: 'New Fields Brand'
  },
  {
    src: new URL('../assets/pinnacle_brand.svg', import.meta.url).href,
    alt: 'Pinnacle Brand'
  }
])
</script>

<template>
  <div class="mx-auto mt-10 w-full max-w-7xl">
    <div class="mb-4 text-center text-sm font-bold tracking-wide text-black/60">Working With :</div>
    <div class="mx-auto rounded-2xl bg-white px-4 py-6 sm:px-6 md:px-8">
      <div class="grid grid-cols-2 gap-4 md:grid-cols-3 lg:grid-cols-6">
        <div
          v-for="brand in workingBrandImages"
          :key="brand.src"
          class="flex items-center justify-center rounded-lg bg-white p-3"
        >
          <img
            :src="brand.src"
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

<script setup lang="ts">
import WhyUsButton from './WhyUsButton.vue'
</script>

<template>
  <div
    class="bg-white text-black text-left py-20 md:py-28 grid items-stretch overflow-hidden md:grid-cols-2"
  >
    <div
      class="order-2 px-6 py-8 text-center md:order-1 md:py-14 md:text-left md:pl-[max(1.5rem,calc((100vw-90rem)/2+1.5rem))] md:pr-8 lg:pl-[max(2rem,calc((100vw-90rem)/2+2rem))]"
    >
      <div class="text-3xl font-bold leading-tight text-black md:text-4xl lg:text-[42px]">
        Renovation <br />
        Backed by <span class="italic text-[#E2722F]">30 Years</span> <br />
        of Expertise
      </div>
      <div class="mx-auto mt-6 max-w-md leading-relaxed text-gray md:mx-0">
        Good Brand brings decades of craftsmanship and real-world expertise to every renovation. We
        listen, guide, and build with precision.
      </div>
      <div class="mt-8">
        <WhyUsButton />
      </div>
    </div>
    <div class="order-1 px-6 md:order-2 md:px-0">
      <img
        src="../assets/room-good-brand-one.png"
        alt="Renovation Expertise"
        class="w-full rounded-2xl object-cover object-left shadow-lg md:h-full md:rounded-none md:shadow-none"
      />
    </div>
  </div>
</template>

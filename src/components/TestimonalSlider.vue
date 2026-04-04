<script setup lang="ts">
import { ref } from 'vue'

const rating = ref({
  src: "data:image/svg+xml,%3csvg%20xmlns='http://www.w3.org/2000/svg'%20viewBox='0%200%2020%2020'%20fill='currentColor'%3e%3cpath%20d='M9.049%202.927c.3-.921%201.603-.921%201.902%200l1.07%203.292a1%201%200%2000.95.69h3.462c.969%200%201.371%201.24.588%201.81l-2.8%202.034a1%201%200%2000-.364%201.118l1.07%203.292c.3.921-.755%201.688-1.54%201.118l-2.8-2.034a1%201%200%2000-1.175%200l-2.8%202.034c-.784.57-1.838-.197-1.539-1.118l1.07-3.292a1%201%200%2000-.364-1.118L2.98%208.72c-.783-.57-.38-1.81.588-1.81h3.461a1%201%200%2000.951-.69l1.07-3.292z'%20/%3e%3c/svg%3e",
  class: 'h-5 w-5',
  width: '20',
  height: '20'
})

const repeatCount = ref(5)
const isHovering = ref(false)
</script>

<template>
  <div
    class="overflow-hidden w-full"
    @mouseenter="isHovering = true"
    @mouseleave="isHovering = false"
  >
    <div
      :class="['text-left flex animate-marquee gap-6', { 'animate-marquee-paused': isHovering }]"
    >
      <template v-for="groupIndex in 2" :key="groupIndex">
        <div class="flex gap-6">
          <div class="w-80 shrink-0 rounded-2xl bg-white p-6 shadow-md">
            <div class="flex gap-1">
              <img
                v-for="index in repeatCount"
                :key="index"
                :src="rating.src"
                :class="rating.class"
                :width="rating.width"
                :height="rating.height"
                alt="Star Rating"
              />
            </div>
            <div class="mt-4 text-sm leading-relaxed text-gray">
              Good Brand made our renovation completely stress-free. They handled everything from
              design to final touches, and the results were better than we imagined.
            </div>
            <div class="mt-4 text-sm font-medium text-black">Jennifer Lee</div>
          </div>
          <div class="w-80 shrink-0 rounded-2xl bg-white p-6 shadow-md">
            <div class="flex gap-1">
              <img
                v-for="index in repeatCount"
                :key="index"
                :src="rating.src"
                :class="rating.class"
                :width="rating.width"
                :height="rating.height"
                alt="Star Rating"
              />
            </div>
            <div class="mt-4 text-sm leading-relaxed text-gray">
              We were impressed by the attention to detail and the craftsmanship. Our living room
              has never looked better. Highly recommend!
            </div>
            <div class="mt-4 text-sm font-medium text-black">Michelle T.</div>
          </div>
          <div class="w-80 shrink-0 rounded-2xl bg-white p-6 shadow-md">
            <div class="flex gap-1">
              <img
                v-for="index in repeatCount"
                :key="index"
                :src="rating.src"
                :class="rating.class"
                :width="rating.width"
                :height="rating.height"
                alt="Star Rating"
              />
            </div>
            <div class="mt-4 text-sm leading-relaxed text-gray">
              Professional team, transparent pricing, and outstanding results. Our bathroom
              renovation was completed ahead of schedule.
            </div>
            <div class="mt-4 text-sm font-medium text-black">David C.</div>
          </div>
          <div class="w-80 shrink-0 rounded-2xl bg-white p-6 shadow-md">
            <div class="flex gap-1">
              <img
                v-for="index in repeatCount"
                :key="index"
                :src="rating.src"
                :class="rating.class"
                :width="rating.width"
                :height="rating.height"
                alt="Star Rating"
              />
            </div>
            <div class="mt-4 text-sm leading-relaxed text-gray">
              The best decision we made was choosing Good Brand for our home renovation. They truly
              care about quality and customer satisfaction.
            </div>
            <div class="mt-4 text-sm font-medium text-black">Priya M.</div>
          </div>
        </div>
      </template>
    </div>
  </div>
</template>

<style>
.animate-marquee {
  animation-name: marquee;
  animation-duration: 10s;
  animation-timing-function: linear;
  animation-delay: 0s;
  animation-iteration-count: infinite;
  animation-direction: normal;
  animation-fill-mode: none;
  animation-play-state: running;
}

.animate-marquee-paused {
  animation-play-state: paused;
}

/* Example keyframes */
@keyframes marquee {
  0% {
    transform: translateX(0);
  }
  100% {
    transform: translateX(-50%);
  }
}

.from-yellow {
  --tw-gradient-from: #ffc247;
}

.to-transparent {
  --tw-gradient-to: transparent;
}
</style>

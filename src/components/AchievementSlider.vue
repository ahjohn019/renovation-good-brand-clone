<script setup lang="ts">
import { ref, computed, onMounted, onUnmounted, nextTick } from 'vue'

const AUTO_PLAY_DELAY = 3000
const MIN_DRAG_THRESHOLD = 50
const DRAG_THRESHOLD_RATIO = 0.15

const images = ref([
  { src: new URL('../assets/slider_image_one.jpg', import.meta.url).href },
  { src: new URL('../assets/slider_image_two.jpg', import.meta.url).href },
  { src: new URL('../assets/slider_image_three.jpg', import.meta.url).href },
  { src: new URL('../assets/slider_image_four.jpg', import.meta.url).href }
])

const visibleCount = ref(3)
const currentIndex = ref(0)
const isTransitioning = ref(true)
let interval: ReturnType<typeof setInterval> | null = null

// Infinite loop clones
const cloneCount = computed(() => visibleCount.value)
const imageLists = computed(() => {
  const before = images.value.slice(-cloneCount.value)
  const after = images.value.slice(0, cloneCount.value)
  return [...before, ...images.value, ...after]
})

const baseIndex = computed(() => cloneCount.value)
const lastRealIndex = computed(() => baseIndex.value + images.value.length - 1)
const sliderRef = ref<HTMLElement | null>(null)
const containerWidth = ref(0)
const startX = ref(0)
const deltaX = ref(0)
const isDragging = ref(false)

// Real index for bullets
const realIndex = computed(() => {
  if (currentIndex.value < baseIndex.value) {
    return images.value.length - (baseIndex.value - currentIndex.value)
  }
  if (currentIndex.value > lastRealIndex.value) {
    return currentIndex.value - baseIndex.value - images.value.length
  }
  return currentIndex.value - baseIndex.value
})

const slideWidth = computed(() => 100 / visibleCount.value)
const slideWidthPx = computed(() =>
  visibleCount.value > 0 ? containerWidth.value / visibleCount.value : 0
)
const trackTranslateX = computed(() => -(currentIndex.value * slideWidthPx.value) + deltaX.value)
const trackStyle = computed(() => ({
  transform: `translateX(${trackTranslateX.value}px)`
}))

// Responsive
const setVisibleCount = () => {
  const width = window.innerWidth
  visibleCount.value = width >= 1024 ? 3 : width >= 640 ? 2 : 1
}

const updateSliderMetrics = () => {
  containerWidth.value = sliderRef.value?.clientWidth ?? 0
}

// Slider controls
const resetIndex = async (target: number) => {
  isTransitioning.value = false
  currentIndex.value = target
  await nextTick()
  requestAnimationFrame(() => {
    isTransitioning.value = true
  })
}

const next = () => currentIndex.value++
const prev = () => currentIndex.value--
const goTo = (index: number) => {
  isTransitioning.value = true
  currentIndex.value = baseIndex.value + index
}

// Infinite loop handling
const handleTransitionEnd = () => {
  if (currentIndex.value > lastRealIndex.value) resetIndex(baseIndex.value)
  else if (currentIndex.value < baseIndex.value) resetIndex(lastRealIndex.value)
}

// Auto-play
const startAutoPlay = () => {
  if (!interval) interval = setInterval(next, AUTO_PLAY_DELAY)
}
const stopAutoPlay = () => {
  if (interval) {
    clearInterval(interval)
    interval = null
  }
}

// Gesture support
const setDraggingCursor = (cursor: '' | 'grabbing') => {
  document.body.style.cursor = cursor
}

const getClientX = (event: MouseEvent | TouchEvent) =>
  'touches' in event ? (event.touches[0]?.clientX ?? 0) : event.clientX

const onDragStart = (event: MouseEvent | TouchEvent) => {
  stopAutoPlay()
  updateSliderMetrics()
  isDragging.value = true
  isTransitioning.value = false
  startX.value = getClientX(event)
  deltaX.value = 0
  setDraggingCursor('grabbing')
}

const onDragMove = (event: MouseEvent | TouchEvent) => {
  if (!isDragging.value) return
  const currentX = getClientX(event)
  deltaX.value = currentX - startX.value
}

const onDragEnd = () => {
  if (!isDragging.value) return
  const threshold = Math.max(MIN_DRAG_THRESHOLD, slideWidthPx.value * DRAG_THRESHOLD_RATIO)
  isTransitioning.value = true
  if (deltaX.value > threshold) prev()
  else if (deltaX.value < -threshold) next()
  deltaX.value = 0
  isDragging.value = false
  setDraggingCursor('')
  startAutoPlay()
}

// Lifecycle
onMounted(() => {
  setVisibleCount()
  currentIndex.value = baseIndex.value
  window.addEventListener('resize', setVisibleCount)
  window.addEventListener('resize', updateSliderMetrics)
  window.addEventListener('mousemove', onDragMove)
  window.addEventListener('mouseup', onDragEnd)
  window.addEventListener('touchmove', onDragMove, { passive: false })
  window.addEventListener('touchend', onDragEnd)
  nextTick(updateSliderMetrics)
  startAutoPlay()
})
onUnmounted(() => {
  window.removeEventListener('resize', setVisibleCount)
  window.removeEventListener('resize', updateSliderMetrics)
  window.removeEventListener('mousemove', onDragMove)
  window.removeEventListener('mouseup', onDragEnd)
  window.removeEventListener('touchmove', onDragMove)
  window.removeEventListener('touchend', onDragEnd)
  setDraggingCursor('')
  stopAutoPlay()
})
</script>

<template>
  <div class="w-full">
    <div
      class="relative w-full overflow-hidden group select-none"
      ref="sliderRef"
      @mouseenter="stopAutoPlay"
      @mouseleave="!isDragging && startAutoPlay()"
      @mousedown.prevent="onDragStart"
      @touchstart.prevent="onDragStart"
      style="touch-action: pan-y"
      :class="{ 'cursor-grab': !isDragging, 'cursor-grabbing': isDragging }"
    >
      <!-- Slides -->
      <div
        class="flex"
        :class="isTransitioning ? 'transition-transform duration-500 ease-in-out' : ''"
        :style="trackStyle"
        @transitionend="handleTransitionEnd"
      >
        <div
          v-for="(item, index) in imageLists"
          :key="index"
          class="flex-shrink-0 flex justify-center items-center px-3 pointer-events-none"
          :style="{ width: slideWidth + '%' }"
        >
          <div class="w-full aspect-[4/3] overflow-hidden rounded-2xl">
            <img
              :src="item.src"
              class="w-full h-full object-cover pointer-events-none"
              width="800"
              height="600"
            />
          </div>
        </div>
      </div>
    </div>

    <!-- Bullets -->
    <div class="mt-6 flex justify-center gap-2">
      <button
        v-for="(_, index) in images"
        :key="index"
        @click="goTo(index)"
        class="h-3 w-3 rounded-full transition-all duration-300"
        :class="realIndex === index ? 'bg-[#ffc247]' : 'bg-[#a7a7a7]'"
      ></button>
    </div>
  </div>
</template>

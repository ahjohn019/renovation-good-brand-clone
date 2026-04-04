<script setup lang="ts">
import { ref, watch, onMounted, onUnmounted } from 'vue'
import QuoteButton from './QuoteButton.vue'

const activeLink = ref('#home')
const isMobileMenuOpen = ref(false)
const DESKTOP_BREAKPOINT = 1024

const navBarLinkClasses = 'transition-colors text-sm font-medium cursor-pointer flex items-center'

const navBarLinks = ref([
  { name: 'Home', href: '#home', class: navBarLinkClasses },
  { name: 'Company', href: '#company', class: navBarLinkClasses },
  { name: 'Projects', href: '#projects', class: navBarLinkClasses },
  { name: 'Services', href: '#services', class: navBarLinkClasses },
  { name: 'FAQ', href: '#faq', class: navBarLinkClasses }
])

const setActiveLink = (href: string) => {
  activeLink.value = href
  isMobileMenuOpen.value = false
}

const toggleMobileMenu = () => {
  isMobileMenuOpen.value = !isMobileMenuOpen.value
}

const closeMobileMenu = () => {
  isMobileMenuOpen.value = false
}

watch(isMobileMenuOpen, (isOpen) => {
  document.body.style.overflow = isOpen ? 'hidden' : ''
})

const handleWindowResize = () => {
  if (window.innerWidth >= DESKTOP_BREAKPOINT && isMobileMenuOpen.value) {
    closeMobileMenu()
  }
}

onMounted(() => {
  window.addEventListener('resize', handleWindowResize)
})

onUnmounted(() => {
  window.removeEventListener('resize', handleWindowResize)
  document.body.style.overflow = ''
})
</script>

<template>
  <nav class="sticky top-0 left-0 right-0 z-[1000] w-full bg-white shadow-sm">
    <div class="flex h-16 items-center justify-between px-4 sm:px-6 lg:h-20">
      <div class="flex items-center">
        <span class="text-2xl font-bold text-gray-800">
          <img src="../assets/good_brand_logo.svg" alt="Logo" class="h-8 w-auto lg:h-10" />
        </span>
      </div>

      <div class="hidden items-center gap-8 lg:flex">
        <div class="flex gap-8 text-black">
          <a
            v-for="(link, index) in navBarLinks"
            :key="index"
            :href="link.href"
            :class="[
              link.class,
              activeLink === link.href ? 'text-[#e85102] font-bold' : 'hover:text-[#e85102]'
            ]"
            @click="setActiveLink(link.href)"
          >
            {{ link.name }}
          </a>
        </div>
        <QuoteButton />
      </div>

      <button
        type="button"
        class="flex h-11 w-11 items-center justify-center text-black transition lg:hidden cursor-pointer"
        :aria-expanded="isMobileMenuOpen"
        aria-label="Toggle navigation menu"
        @click="toggleMobileMenu"
      >
        <svg
          xmlns="http://www.w3.org/2000/svg"
          viewBox="0 0 24 24"
          fill="none"
          stroke="currentColor"
          stroke-width="2"
          class="h-6 w-6"
        >
          <path stroke-linecap="round" d="M4 7h16M4 12h16M4 17h16" />
        </svg>
      </button>
    </div>

    <Transition
      enter-active-class="transition-opacity duration-300 ease-out"
      enter-from-class="opacity-0"
      enter-to-class="opacity-100"
      leave-active-class="transition-opacity duration-200 ease-in"
      leave-from-class="opacity-100"
      leave-to-class="opacity-0"
    >
      <div v-if="isMobileMenuOpen" class="fixed inset-0 z-[1100] lg:hidden">
        <button
          type="button"
          class="absolute inset-0 bg-black/40 backdrop-blur-[2px]"
          aria-label="Close navigation menu"
          @click="closeMobileMenu"
        ></button>

        <Transition
          enter-active-class="transition-transform duration-300 ease-out"
          enter-from-class="translate-x-full"
          enter-to-class="translate-x-0"
          leave-active-class="transition-transform duration-200 ease-in"
          leave-from-class="translate-x-0"
          leave-to-class="translate-x-full"
        >
          <div
            v-if="isMobileMenuOpen"
            class="absolute right-0 top-0 flex h-full w-[min(18rem,88vw)] flex-col bg-white px-5 py-6 shadow-2xl"
          >
            <div class="mb-8 flex items-center justify-between">
              <img src="../assets/good_brand_logo.svg" alt="Logo" class="h-8 w-auto" />
              <button
                type="button"
                class="flex h-10 w-10 items-center justify-center text-black transition hover:bg-black/5"
                aria-label="Close navigation menu"
                @click="closeMobileMenu"
              >
                <svg
                  xmlns="http://www.w3.org/2000/svg"
                  viewBox="0 0 24 24"
                  fill="none"
                  stroke="currentColor"
                  stroke-width="2"
                  class="h-5 w-5"
                >
                  <path stroke-linecap="round" d="M6 6l12 12M18 6L6 18" />
                </svg>
              </button>
            </div>

            <div class="flex flex-1 flex-col gap-4 text-black">
              <a
                v-for="(link, index) in navBarLinks"
                :key="index"
                :href="link.href"
                :class="[
                  'rounded-xl px-3 py-2 text-left font-medium transition-colors',
                  activeLink === link.href ? 'text-[#e85102]' : 'hover:text-[#e85102]'
                ]"
                @click="setActiveLink(link.href)"
              >
                {{ link.name }}
              </a>
            </div>

            <div class="mt-6">
              <QuoteButton />
            </div>
          </div>
        </Transition>
      </div>
    </Transition>
  </nav>
</template>

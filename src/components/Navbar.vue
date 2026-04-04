<script setup lang="ts">
import { ref } from 'vue'
import QuoteButton from './QuoteButton.vue'

const activeLink = ref('#home')

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
}
</script>

<template>
  <nav
    class="sticky top-0 left-0 right-0 w-full h-16 lg:h-20 bg-white flex justify-between items-center px-6"
  >
    <!-- Logo -->
    <div class="flex items-center">
      <span class="text-2xl font-bold text-gray-800">
        <img src="../assets/good_brand_logo.svg" alt="Logo" class="h-8 w-auto lg:h-10" />
      </span>
    </div>
    <div class="items-center flex gap-8">
      <nav class="flex gap-8 text-black">
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
      </nav>
      <QuoteButton />
    </div>
  </nav>
</template>

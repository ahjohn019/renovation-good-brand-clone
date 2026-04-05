<script setup lang="ts">
import VideoContainer from './VideoContainer.vue'
import RenovationFeatures from './RenovationFeatures.vue'
import Testimonal from './Testimonal.vue'
import Achievement from './Achievement.vue'
import Footer from './Footer.vue'
import whatsappIcon from '../assets/whatsapp_icon.svg'
</script>

<template>
  <div class="w-full">
    <VideoContainer />
    <RenovationFeatures />
    <Testimonal />
    <Achievement />
    <Footer />

    <a
      href="https://wa.me/60123693499"
      target="_blank"
      rel="noopener noreferrer"
      aria-label="Chat with Good Brand on WhatsApp"
      class="fixed bottom-5 right-5 z-[1000]"
    >
      <img
        :src="whatsappIcon"
        alt="WhatsApp"
        class="h-12 w-12 transition-transform duration-200 hover:scale-[1.2]"
      />
    </a>
  </div>
</template>

<template>
  <footer class="bg-black pt-16 pb-8">
    <div class="max-w-7xl mx-auto px-4 md:px-6 lg:px-0">
      <img
        src="../assets/sub_good_brand_logo.svg"
        alt=""
        width="120"
        height="40"
        class="mx-auto h-10 w-auto lg:mx-0"
      />
      <div class="mt-10 grid gap-12 lg:grid-cols-3 text-left text-xs">
        <div class="col-span-1 grid grid-cols-[1fr_auto] gap-8 lg:col-span-2 lg:grid-cols-2">
          <div>
            <div class="font-semibold uppercase tracking-widest text-white/50">Contact Us</div>
            <div class="mt-4 flex flex-col gap-4 text-sm">
              <a href="tel:012-3693499" class="text-white/80 hover:text-white"
                ><span class="text-white/50">Mobile: </span> 012-3693499</a
              >
              <a href="tel:03-6252 0880" class="text-white/80 hover:text-white"
                ><span class="text-white/50">Office: </span> 03-6252 0880</a
              >
              <a href="mailto:goodbrand.reno@gmail.com" class="text-white/80 hover:text-white"
                ><span class="text-white/50">Email: </span> goodbrand.reno@gmail.com</a
              >
              <a href="" class="text-white/80 hover:text-white"
                ><span class="text-white/50">Operating Hours: </span> 9AM - 6PM</a
              >
            </div>
          </div>
          <div>
            <div class="font-semibold uppercase tracking-widest text-white/50">Quick Links</div>
            <div class="mt-4 flex flex-col gap-3 text-sm">
              <a href="/" class="text-white/80 hover:text-white">Home</a>
              <a href="/company" class="text-white/80 hover:text-white">Company</a>
              <a href="/projects" class="text-white/80 hover:text-white">Projects</a>
              <a href="/services" class="text-white/80 hover:text-white">Services</a>
              <a href="/contact" class="text-white/80 hover:text-white">Contact</a>
            </div>
          </div>
        </div>
        <div class="relative overflow-hidden rounded-2xl bg-[#ffc247] p-6 shadow-lg">
          <div class="flex justify-between">
            <div>
              <div class="text-xl font-medium text-black">Book Appointment</div>
              <div class="mt-2 pr-12 text-xs leading-relaxed text-black/60">
                Schedule a free consultation and get expert guidance for your home project.
              </div>
            </div>
            <a href="https://wa.me/60123693499" target="_blank" rel="noopener noreferrer">
              <img
                src="../assets/whatsapp_icon.svg"
                alt="WhatsApp Icon"
                width="70"
                height="70"
                class="mb-4"
              />
            </a>
          </div>
          <form class="mt-4 flex items-center">
            <input
              type="tel"
              name="phone"
              placeholder="Phone Number"
              class="flex-1 rounded-l-full border-0 bg-white px-5 py-2.5 text-sm text-black placeholder:text-gray-light focus:ring-2 focus:ring-orange focus:outline-none"
            />
            <button
              type="submit"
              class="rounded-r-full bg-black px-6 py-2.5 text-sm font-bold text-white transition-colors hover:bg-gray disabled:opacity-50"
            >
              Submit
            </button>
          </form>
        </div>
      </div>
      <div
        class="mt-14 flex flex-col gap-4 justify-between items-center border-t border-white/10 pt-8 sm:flex-row"
      >
        <div class="flex gap-6">
          <div class="flex items-center gap-6">Follow Us</div>
          <div class="flex gap-2">
            <a href="https://facebook.com/goodbrand">
              <img src="../assets/facebook_icon.svg" alt="Facebook" width="25" height="25" />
            </a>
            <a href="https://instagram.com/goodbrand">
              <img src="../assets/instagram_icon.svg" alt="Instagram" width="25" height="25" />
            </a>
            <a href="https://tiktok.com/@goodbrand">
              <img src="../assets/tiktok_icon.svg" alt="TikTok" width="25" height="25" />
            </a>
          </div>
        </div>
        <div class="flex gap-4">
          <a href="/privacy" class="text-sm text-white/50 hover:text-white underline"
            >Privacy Policy</a
          >
          <a href="/terms" class="text-sm text-white/50 hover:text-white underline"
            >Terms of Service</a
          >
        </div>
      </div>
      <div class="mt-6 border-t border-white/5 pt-6 text-center text-xs text-white/50">
        Copyright © 2026 Good Brand Sdn Bhd. All rights reserved
      </div>
    </div>
  </footer>
</template>

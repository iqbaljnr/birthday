<script setup>
import { onMounted } from 'vue';
import { gsap } from 'gsap';
import { ScrollTrigger } from 'gsap/ScrollTrigger';

gsap.registerPlugin(ScrollTrigger);

onMounted(() => {
  gsap.from('.message-card', {
    scrollTrigger: {
      trigger: '.message-container',
      start: 'top 70%',
    },
    scale: 0.9,
    opacity: 0,
    duration: 1,
    ease: 'elastic.out(1, 0.5)'
  });
});
</script>

<template>
  <section id="open-letter" class="py-32 px-6 bg-[#fff8f0] relative overflow-hidden">
    <!-- Background pattern -->
    <div class="absolute inset-0 opacity-[0.03]" style="background-image: url('data:image/svg+xml,%3Csvg width=\'60\' height=\'60\' viewBox=\'0 0 60 60\' xmlns=\'http://www.w3.org/2000/svg\'%3E%3Cg fill=\'none\' fill-rule=\'evenodd\'%3E%3Cg fill=\'%23000000\' fill-opacity=\'1\'%3E%3Cpath d=\'M36 34v-4h-2v4h-4v2h4v4h2v-4h4v-2h-4zm0-30V0h-2v4h-4v2h4v4h2V6h4V4h-4zM6 34v-4H4v4H0v2h4v4h2v-4h4v-2H6zM6 4V0H4v4H0v2h4v4h2V6h4V4H6z\'/%3E%3C/g%3E%3C/g%3E%3C/svg%3E');"></div>

    <div class="max-w-4xl mx-auto relative z-10 message-container flex flex-col items-center">
      <div class="message-card bg-white p-8 md:p-14 rounded-[3rem] shadow-xl border border-pink-100 text-center relative">
        <!-- Decorative quote mark -->
        <span class="absolute -top-6 -left-2 text-8xl text-pink-200 font-serif leading-none select-none">"</span>
        
        <h2 class="text-3xl md:text-5xl font-bold text-gray-800 heading-font mb-8">An Open Letter to You</h2>
        
        <p class="text-xl md:text-2xl text-gray-600 leading-relaxed italic mb-8">
          You bring so much light and happiness into the world. Every moment spent with you is a treasure, and I couldn't be more grateful. May this year bring you closer to all your dreams.
        </p>
        
        <div class="w-16 h-1 bg-pink-300 mx-auto rounded-full mb-6"></div>
        
        <p class="font-bold text-gray-800 text-lg uppercase tracking-widest">- Thal & Blakk</p>
      </div>
    </div>
  </section>
</template>

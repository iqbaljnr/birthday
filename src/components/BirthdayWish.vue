<script setup>
import { onMounted } from 'vue';
import { gsap } from 'gsap';
import { ScrollTrigger } from 'gsap/ScrollTrigger';

gsap.registerPlugin(ScrollTrigger);

onMounted(() => {
  gsap.from('.final-text > *', {
    scrollTrigger: {
      trigger: '.final-wish-section',
      start: 'top 80%',
    },
    y: 30,
    opacity: 0,
    duration: 1,
    stagger: 0.3,
    ease: 'power2.out'
  });
});
</script>

<template>
  <section class="final-wish-section py-32 px-6 bg-gradient-to-b from-white to-[#fff1f2] text-center min-h-[60vh] flex flex-col justify-center items-center">
    <div class="max-w-3xl mx-auto final-text">
      <h2 class="text-3xl md:text-5xl font-bold text-gray-800 heading-font mb-8">One Last Wish...</h2>
      
      <p class="text-lg md:text-2xl text-gray-600 leading-relaxed mb-6">
       Makasih udah lahir vey, tahan tahan didunia ya
      </p>
      
      <p class="text-lg md:text-2xl text-gray-600 leading-relaxed mb-12">
        Happy Birthday, and here's to many, many more amazing years ahead.
      </p>
      
      <div class="text-pink-400">
        <svg class="w-12 h-12 mx-auto animate-pulse" fill="currentColor" viewBox="0 0 20 20">
          <path fill-rule="evenodd" d="M3.172 5.172a4 4 0 015.656 0L10 6.343l1.172-1.171a4 4 0 115.656 5.656L10 17.657l-6.828-6.829a4 4 0 010-5.656z" clip-rule="evenodd"></path>
        </svg>
      </div>
    </div>
  </section>
</template>

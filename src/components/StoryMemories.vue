<script setup>
import { onMounted } from 'vue';
import { gsap } from 'gsap';
import { ScrollTrigger } from 'gsap/ScrollTrigger';

gsap.registerPlugin(ScrollTrigger);

import memory1 from '../assets/1.jpeg';
import memory2 from '../assets/2.jpeg';
import memory3 from '../assets/3.jpeg';

// Placeholder photos for visual
const memories = [
  { id: 1, type: 'image', src: memory1, alt: 'Memory 1', span: 'col-span-2 md:col-span-2 row-span-2' },
  { id: 2, type: 'image', src: memory2, alt: 'Memory 2', span: 'col-span-1 md:col-span-2 row-span-1' },
  { id: 3, type: 'image', src: memory3, alt: 'Memory 3', span: 'col-span-1 md:col-span-2 row-span-1' },
];

onMounted(() => {
  gsap.from('.memory-item', {
    scrollTrigger: {
      trigger: '.memories-container',
      start: 'top 80%',
    },
    y: 100,
    opacity: 0,
    duration: 0.8,
    stagger: 0.2,
    ease: 'power3.out'
  });
});
</script>

<template>
  <section class="py-24 px-6 bg-white relative">
    <div class="max-w-6xl mx-auto memories-container">
      <div class="text-center mb-16">
        <h2 class="text-4xl md:text-5xl font-bold text-gray-800 heading-font mb-4">Moments of You</h2>
        <p class="text-gray-500 max-w-2xl mx-auto text-lg">A few moments that capture your energy, your smile, and the way you see the world.</p>
      </div>

      <div class="grid grid-cols-2 md:grid-cols-4 gap-4 md:gap-6 auto-rows-[200px]">
        <div 
          v-for="memory in memories" 
          :key="memory.id" 
          :class="['memory-item relative rounded-3xl overflow-hidden group shadow-lg', memory.span]"
        >
          <img :src="memory.src" :alt="memory.alt" class="w-full h-full object-cover transition-transform duration-700 group-hover:scale-110" />
          
          <div class="absolute inset-0 bg-gradient-to-t from-black/60 via-black/20 to-transparent opacity-0 group-hover:opacity-100 transition-opacity duration-300 flex items-end p-6">
            <div class="text-white">
              <p class="font-medium text-lg">Beautiful moment</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

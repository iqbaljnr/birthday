<script setup>
import { onMounted } from 'vue';
import { gsap } from 'gsap';
import { ScrollTrigger } from 'gsap/ScrollTrigger';
import { Heart, Star, Sparkles, Smile, Sun, Music } from 'lucide-vue-next';

gsap.registerPlugin(ScrollTrigger);

const traits = [
  { id: 1, title: 'Your Smile', description: 'It literally lights up any room you walk into.', icon: Smile, color: 'text-amber-500', bg: 'bg-amber-100' },
  { id: 2, title: 'Your Kindness', description: 'The gentle and pure way you treat everyone around you.', icon: Heart, color: 'text-pink-500', bg: 'bg-pink-100' },
  { id: 3, title: 'Your Energy', description: 'Vibrant, warm, and absolutely contagious.', icon: Sun, color: 'text-orange-500', bg: 'bg-orange-100' },
  { id: 4, title: 'Your Humor', description: 'Always knowing how to make me laugh even on bad days.', icon: Sparkles, color: 'text-purple-500', bg: 'bg-purple-100' },
  { id: 5, title: 'Your Passion', description: 'The way your eyes shine when you talk about things you love.', icon: Star, color: 'text-yellow-500', bg: 'bg-yellow-100' },
  { id: 6, title: 'Your Taste in Music', description: '(mostly...) Just kidding, it’s actually pretty great.', icon: Music, color: 'text-blue-500', bg: 'bg-blue-100' },
];

onMounted(() => {
  gsap.from('.trait-card', {
    scrollTrigger: {
      trigger: '.appreciate-container',
      start: 'top 70%',
    },
    y: 0,
    opacity: 1,
    duration: 0.6,
    stagger: 0.15,
    ease: 'power2.out'
  });
});
</script>

<template>
  <section class="py-24 px-6 bg-white relative">
    <div class="max-w-6xl mx-auto appreciate-container">
      <div class="text-center mb-16">
        <h2 class="text-4xl md:text-5xl font-bold text-gray-800 heading-font mb-4">Things I Appreciate About You</h2>
        <p class="text-gray-500 max-w-2xl mx-auto text-lg">Just a few of the million reasons why you're so special.</p>
      </div>

      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
        <div 
          v-for="trait in traits" 
          :key="trait.id"
          class="trait-card p-8 rounded-3xl border border-gray-100 shadow-sm hover:shadow-lg transition-all duration-300 bg-white group hover:-translate-y-2"
        >
          <div :class="['w-14 h-14 rounded-2xl flex items-center justify-center mb-6 transition-transform group-hover:scale-110', trait.bg, trait.color]">
            <component :is="trait.icon" class="w-7 h-7" />
          </div>
          <h3 class="text-2xl font-bold text-gray-800 mb-3">{{ trait.title }}</h3>
          <p class="text-gray-600 leading-relaxed">{{ trait.description }}</p>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, onMounted } from 'vue';
import { gsap } from 'gsap';
import confetti from 'canvas-confetti';

import TaylorSwiftMusic from '../assets/Taylor_Swift.mp3';

const isMusicPlaying = ref(false);
const audioRef = ref(null);

const triggerSurprise = () => {
  // Confetti explosion
  const defaults = { startVelocity: 30, spread: 360, ticks: 60, zIndex: 0 };
  
  const randomInRange = (min, max) => Math.random() * (max - min) + min;

  const interval = setInterval(function() {
    const particleCount = 50;
    confetti({
      ...defaults, particleCount,
      origin: { x: randomInRange(0.1, 0.3), y: Math.random() - 0.2 }
    });
    confetti({
      ...defaults, particleCount,
      origin: { x: randomInRange(0.7, 0.9), y: Math.random() - 0.2 }
    });
  }, 250);

  setTimeout(() => clearInterval(interval), 3000);

  // Animate Cake
  gsap.to('.birthday-cake', {
    scale: 1.1,
    rotation: 5,
    yoyo: true,
    repeat: 5,
    duration: 0.2,
    ease: 'power1.inOut'
  });

  // Toggle Music (if it was implemented with an actual src)
  if (audioRef.value) {
    if (isMusicPlaying.value) {
      audioRef.value.pause();
    } else {
      audioRef.value.play().catch(e => console.log('Audio play failed:', e));
    }
    isMusicPlaying.value = !isMusicPlaying.value;
  }
};

const scrollToNext = () => {
  document.getElementById('open-letter')?.scrollIntoView({ behavior: 'smooth' });
};

onMounted(() => {
  // GSAP Animation
  gsap.from('.hero-content > *', {
    y: 50,
    opacity: 0,
    duration: 1,
    stagger: 0.2,
    ease: 'power3.out'
  });
});
</script>

<template>
  <section class="min-h-screen relative flex items-center justify-center p-6 bg-gradient-to-br from-[#fff1f2] to-[#fce7f3] overflow-hidden">
    <!-- Decorative blobs -->
    <div class="absolute top-[-10%] left-[-10%] w-96 h-96 bg-[#fbcfe8] rounded-full mix-blend-multiply filter blur-3xl opacity-50 animate-blob"></div>
    <div class="absolute top-[20%] right-[-10%] w-96 h-96 bg-[#fef08a] rounded-full mix-blend-multiply filter blur-3xl opacity-50 animate-blob animation-delay-2000"></div>

    <div class="hero-content relative z-10 text-center max-w-4xl mx-auto">
      <h2 class="text-xl md:text-2xl text-pink-500 font-medium mb-4 uppercase tracking-widest">A special day for</h2>
      <h1 class="text-6xl md:text-8xl font-bold text-gray-800 mb-6 heading-font leading-tight">
        Happy Birthday <br /> <span class="text-transparent bg-clip-text bg-gradient-to-r from-pink-500 to-orange-400">Navey!</span>
      </h1>
      
      <p class="text-gray-600 text-lg md:text-xl mb-12 max-w-2xl mx-auto">
        May your day be filled with joy, laughter, and endless beautiful memories. Here's a little something crafted just for you.
      </p>

      <div class="flex flex-col sm:flex-row items-center justify-center gap-4 mx-auto">
        <button @click="triggerSurprise" class="px-8 py-3 bg-white text-pink-500 font-bold rounded-full shadow-md hover:bg-pink-50 transition border border-pink-100 flex items-center justify-center gap-2">
          <svg v-if="!isMusicPlaying" class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M14.752 11.168l-3.197-2.132A1 1 0 0010 9.87v4.263a1 1 0 001.555.832l3.197-2.132a1 1 0 000-1.664z"></path><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M21 12a9 9 0 11-18 0 9 9 0 0118 0z"></path></svg>
          <svg v-else class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M10 9v6m4-6v6m7-3a9 9 0 11-18 0 9 9 0 0118 0z"></path></svg>
          {{ isMusicPlaying ? 'Stop Music' : 'Play Music & Celebrate' }}
        </button>

        <button @click="scrollToNext" class="group relative inline-flex items-center justify-center px-8 py-3 font-bold text-white transition-all duration-200 bg-pink-500 rounded-full hover:bg-pink-600 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-pink-500 hover:scale-105 active:scale-95 shadow-md shadow-pink-500/30">
          Open Letter
          <svg class="w-5 h-5 ml-2 transition-transform group-hover:translate-y-1" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 14l-7 7m0 0l-7-7m7 7V3"></path>
          </svg>
        </button>
      </div>

      <!-- Hidden Audio element -->
      <!-- Add actual music src here -->
      <audio ref="audioRef" loop>
        <source :src="TaylorSwiftMusic" type="audio/mpeg">
      </audio>
    </div>
  </section>
</template>

<style scoped>
.birthday-cake svg {
  transition: filter 0.3s;
}
.birthday-cake:hover svg {
  filter: brightness(1.1);
}

@keyframes blob {
  0% { transform: translate(0px, 0px) scale(1); }
  33% { transform: translate(30px, -50px) scale(1.1); }
  66% { transform: translate(-20px, 20px) scale(0.9); }
  100% { transform: translate(0px, 0px) scale(1); }
}
.animate-blob {
  animation: blob 7s infinite;
}
.animation-delay-2000 {
  animation-delay: 2s;
}
</style>

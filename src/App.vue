<script setup>
import { onMounted } from 'vue';
import { gsap } from 'gsap';
import { ScrollTrigger } from 'gsap/ScrollTrigger';

import LandingSection from './components/LandingSection.vue';
import OpenLetter from './components/OpenLetter.vue';
import StoryMemories from './components/StoryMemories.vue';
import ThingsIAppreciate from './components/ThingsIAppreciate.vue';
import BirthdayWish from './components/BirthdayWish.vue';

gsap.registerPlugin(ScrollTrigger);

onMounted(() => {
  // We can add global scroll trigger refreshes here if needed
});
</script>

<template>
  <main class="min-h-screen bg-[var(--color-birthday-bg)] overflow-hidden font-sans text-[var(--color-birthday-text)]">
    <LandingSection />
    <OpenLetter />
    <StoryMemories />
    <ThingsIAppreciate />
    <BirthdayWish />
  </main>
</template>

<style>
/* Global styles can also go here, but we use style.css for Tailwind primarily */
</style>

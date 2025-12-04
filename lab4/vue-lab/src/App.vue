<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <header class="fixed top-0 left-0 w-full bg-white shadow-sm z-50">
    <nav class="w-full flex justify-center gap-8 text-gray-600 p-4 font-medium">
      <RouterLink to="/" class="hover:text-red-500 transition">Home</RouterLink>
      <RouterLink to="/about" class="hover:text-red-500 transition">About</RouterLink>
      <RouterLink to="/contact" class="hover:text-red-500 transition">Contact</RouterLink>
      <RouterLink to="/intro" class="hover:text-red-500 transition text-red-500">Intro</RouterLink>
    </nav>
  </header>

  <main class="pt-[80px]">
    <RouterView />
  </main>
</template>

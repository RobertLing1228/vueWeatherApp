<template>
  <header class="sticky top-0 bg-weather-primary shadow-lg">
    <nav
      class="container flex flex-col sm:flex-row items-center gap-4 text-white py-6"
    >
      <RouterLink :to="{ name: 'home' }">
        <div class="flex items-center gap-3 flex-1">
          <i class="fa-regular fa-sun text-2xl"></i>
          <span class="text-2xl">The Local Weather</span>
        </div>
      </RouterLink>
      <!-- Add Icons using String format -->
      
      <div class="flex gap-3 flex-1 justify-end">
        <i class="fa-solid fa-circle-info text-2xl hover:text-weather-secondary duration-150 cursor-pointer"></i>  
        <i class="fa-solid fa-plus text-2xl hover:text-weather-secondary duration-150 cursor-pointer"></i>  
      </div>
    </nav>
  </header>
</template>

<script setup>
import { RouterLink } from "vue-router";
</script>
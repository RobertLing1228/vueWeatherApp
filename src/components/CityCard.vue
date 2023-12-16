<template>
  <div
    class="flex px-3 py-6 rounded-md shadow-md cursor-pointer bg-weather-secondary"
  >
    <div class="flex flex-col flex-1">
      <h2 class="text-3xl">{{ city.city }}</h2>
      <h3>{{ city.state }}</h3>
    </div>

    <div class="flex flex-col gap-2">
      <p class="self-end text-3xl">
        {{ toDegree(city.weather.main.temp) }}&deg;C
      </p>
      <div class="flex gap-2">
        <span class="text-xs">
          H:
          {{ toDegree(city.weather.main.temp_max) }}&deg;C
        </span>
        <span class="text-xs">
          L:
          {{ toDegree(city.weather.main.temp_min) }}&deg;C
        </span>
      </div>
    </div>
  </div>
</template>

<script setup>
import { toDegree } from '@/composition/ToDegree';
defineProps({
  city: {
    type: Object,
    default: () => {},
  },
});
</script>

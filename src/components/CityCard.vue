<template>
  <div
    class="relative flex px-3 py-6 overflow-hidden transition-all duration-300 rounded-md shadow-md cursor-pointer hover:-translate-y-2 bg-blend-lighten hover:bg-blend-darken"
    :style="unsplashImg"
  >
    <div class="flex flex-col flex-1 bg-transparent">
      <h2 class="text-3xl">{{ city.city }}</h2>
      <h3>{{ city.state }}</h3>
    </div>

    <div class="flex flex-col gap-2 bg-transparent">
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
import { toDegree } from "@/composition/ToDegree";
import { createApi } from "unsplash-js";
import { computed, onMounted, onUpdated, ref } from "vue";

const unsplashImg = ref(null);
const ImgData = ref(null);

const props = defineProps({
  city: {
    type: Object,
    default: () => {},
  },
});

onMounted(() => {
  const api = createApi({
    accessKey: "rk3BRArrWJF9bseIDoSj87P7EDGpmisARbNeBRbb5LA",
  });

  const imgQuery = props.city.city + ", " + props.city.state + " park";

  const imageResult = api.search
    .getPhotos({ query: imgQuery, orientation: "landscape", perPage: 1 })
    .then((result) => {
      ImgData.value = result.response.results[0];
      unsplashImg.value =
        "background-image: url('" +
        ImgData.value.urls.regular +
        "'); background-size: cover; background-position: center; background-repeat: no-repeat;";
    })
    .catch((err) => {
      // console.log("something went wrong!");
      console.log(err);
    });

  // unsplashImg.value = imageResult.response.results[0];
});
// computed(() => {
//   unsplashImg.value = ImgData.urls.regular;
// });
</script>

<script setup>
import { ref } from "vue";
import SearchInput from "./components/SearchInput.vue";
import WeatherCard from "./components/WeatherCard.vue";

const places = ref([]);

const addPlace = (data) => {
  console.log(data);
  places.value.push(data);
};
</script>

<template>
  <main>
    <!-- Date get local date-->
    <div class="text-center mb-6">
      {{
        new Date().toLocaleDateString("en-US", {
          weekday: "long",
          year: "numeric",
          month: "long",
          day: "numeric",
        })
      }}
    </div>
    <!-- search -->
    <div>
      <SearchInput @place-data="addPlace" />
    </div>
    <!-- weather Card -->
    <div v-for="(place, idx) in places" :key="idx">
      <WeatherCard :place="place" />
    </div>
  </main>
</template>

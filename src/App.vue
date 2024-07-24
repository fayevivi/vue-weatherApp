<script setup>
import { ref } from "vue";
import SearchInput from "./components/SearchInput.vue";
import WeatherCard from "./components/WeatherCard.vue";

const places = ref([]);

const addPlace = (data) => {
  console.log(data);
  places.value.push(data);
};

const deletePlace = (name) => {
  if (confirm("Are you sure")) {
    places.value = places.value.filter((p) => p.location.name != name);
  }
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
    <div class="grid grid-cols-2 gap-4">
      <div v-for="(place, idx) in places" :key="idx">
        <WeatherCard :place="place" @delete-place="deletePlace" />
      </div>
    </div>
  </main>
</template>

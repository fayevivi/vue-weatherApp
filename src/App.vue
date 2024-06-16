<script setup>
import { ref } from "vue";
import SearchInput from "./components/SearchInput.vue";

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
    <div>
      <p v-for="place in places">
        {{ place.location.name }}
      </p>
    </div>
  </main>
</template>

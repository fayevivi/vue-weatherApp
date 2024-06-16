<script setup>
import { reactive } from "vue";

const searchTerm = reactive({
  query: "",
  timeOut: null,
  results: null,
});

const handleSearch = () => {
  clearTimeout(searchTerm.timeOut);
  // 每半秒鐘做一次動作，且做之前會先清除。以防止做太多次動作。kind of create a lazyLoad or debounce
  searchTerm.timeOut = setTimeout(async () => {
    if (searchTerm.query !== "") {
      const res = await fetch(
        `http://api.weatherapi.com/v1/current.json?key=277148df68ba479da4b91245241606&q=${searchTerm.query}`
      );
      const data = await res.json();
      searchTerm.results = data;
    }
  }, 500);
};
</script>

<template>
  <div>
    <!-- search field -->
    <form>
      <div
        class="bg-white border border-indigo-600/30 rounded-lg shadow-lg flex items-center"
      >
        <i class="fa-solid fa-magnifying-glass p-2 text-indigo-600"></i>
        <input
          type="text"
          placeholder="Search for a place"
          class="rounded-r-lg p-2 border-0 outline-0 focus:ring-2 focus:ring-indigo-600 ring-inset w-full"
          v-model="searchTerm.query"
          @input="handleSearch()"
        />
      </div>
    </form>
    <!-- search suggestions -->
    <div class="bg-white my-2 rounded-lg shadow-lg">
      <div>
        <div>
          <button
            class="px-3 my-2 hover:text-indigo-600 hover:font-bold w-full text-left"
          ></button>
        </div>
      </div>
    </div>
  </div>
</template>

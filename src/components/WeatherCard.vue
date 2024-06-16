<script setup></script>

<template>
  <div
    class="text-white p-10 rounded-lg shadow-lg gap-6 mb-6 relative overflow-hidden"
  >
    <!-- Location & time -->
    <div class="mb-2 flex justify-between items-center">
      <div class="flex items-center justify-center gap-2">
        <i class="fa-solid fa-location-dot"></i>
        <h1 class="text-3xl"></h1>
      </div>
      <div class="flex items-center justify-center gap-2">
        <i class="fa-solid fa-clock"></i>
        <h1 class="text-3xl"></h1>
      </div>
    </div>

    <!-- current weather -->
    <div class="text-center flex-1">
      <img class="mx-auto -mb-10" />
      <h1 class="text-9xl mb-2 -mr-4"></h1>
      <p class="text-2xl"></p>
    </div>

    <!-- forecast -->
    <div></div>

    <div></div>

    <!-- forecast btn -->
    <div class="flex justify-end items-center gap-1 mt-10">
      <button>
        More <i class="fa-solid fa-arrow-right text-sm -mb-px"></i>
      </button>
    </div>
  </div>
</template>

<style scoped>
.bg-day {
  background-color: #8ec5fc;
  background-image: linear-gradient(62deg, #8ec5fc 0%, #e0c3fc 100%);
}
.bg-night {
  background-color: #07223d;
  background-image: linear-gradient(62deg, #0a2a4a 0%, #270845 100%);
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.2s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
</style>

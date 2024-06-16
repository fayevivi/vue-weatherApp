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
  </main>
</template>

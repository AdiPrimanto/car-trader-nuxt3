<template>
  <div>
    <div class="mt-32 flex">
      <!-- * CARS SIDE BAR -->
      <CarSideBar />

      <NuxtPage />
    </div>
  </div>
</template>

<script setup lang="ts">
const route = useRoute();
const { toTitleCase } = useUtilities();

useHead({
  title: `${
    route.params.make ? toTitleCase(route.params.make) : "Cars"
  } in ${toTitleCase(route.params.city)}`,
});

definePageMeta({
  layout: "custom",
});
</script>

<!-- [[make]] -> opsional bisa dinamis atau tidak -->

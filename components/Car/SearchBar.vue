<template>
  <div
    class="font-serif w-full text-2xl rounded-full bg-white flex justify-between overflow-hidden drop-shadow-2xl mx-auto"
    :class="cityError ? 'border border-red-500' : ''"
  >
    <input
      v-model="city"
      type="text"
      class="py-3 px-5 w-full text-2xl rounded-full focus:outline-none"
      placeholder="Search by city..."
    />
    <button @click="handleSearch" class="bg-sky-500 px-10 text-white">
      Search
    </button>
  </div>
</template>

<script setup lang="ts">
const city = ref("");
const cityError = ref(false);

const handleSearch = () => {
  if (!city.value) return (cityError.value = true);
  navigateTo(`/city/${city.value}/car`);
};
</script>

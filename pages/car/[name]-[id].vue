<template>
  <div v-if="car">
    <!-- * CAR HERO -->
    <CarDetailHero :car="car" />

    <!-- * CAR ATTRIBUTES -->
    <CarDetailAttributes :features="car.features" />

    <!-- * CAR DESCRIPTION -->
    <CarDetailDescription :description="car.description" />

    <!-- * CAR CONTACT -->
    <CarDetailContact />
  </div>
</template>

<script setup lang="ts">
const route = useRoute();
const { cars } = useCars();
const { toTitleCase } = useUtilities();

useHead({
  title: `${toTitleCase(route.params.name)}`,
});

const car = computed(() => {
  return cars.find((c) => {
    return c.id === parseInt(route.params.id);
  });
});

if (!car.value) {
  throw createError({
    statusCode: 404,
    message: `Car with ID ${route.params.id} does not exist`,
  });
}

definePageMeta({
  layout: "custom",
});
</script>

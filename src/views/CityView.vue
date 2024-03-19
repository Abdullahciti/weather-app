<template>
  <div>
    <Suspense>
      <AsyncCityView />
      <template #fallback>
        <div class="w-full flex flex-col items-center text-white bg-weather-secondry text-2xl border-r-red-500 mt-10">
          Loading...
        </div>
      </template>
    </Suspense>
  </div>
</template>

<script setup>
import AsyncCityView from "@/components/AsyncCityView.vue";
</script>

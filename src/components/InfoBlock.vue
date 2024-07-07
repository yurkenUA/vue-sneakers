<script setup>
defineProps({
  title: String,
  imageUrl: String,
  desc: String
})
</script>

<template>
  <div class="flex flex-col justify-center items-center text-center w-72 mx-auto">
    <img style="width: 100px; height: 100px" class="" :src="imageUrl" :alt="title" />
    <h2 class="mt-4 text-2xl font-medium">{{ title }}</h2>
    <p class="text-gray-400 mt-2">{{ desc }}</p>
  </div>
</template>

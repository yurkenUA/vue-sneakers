<script setup>
import axios from 'axios'
import { onMounted, ref } from 'vue'

import CardList from '../components/CardList.vue'

const favorites = ref([])

onMounted(async () => {
  try {
    const { data } = await axios.get(
      `https://79da9b92723d58b9.mokky.dev/favorites?_relations=items`
    )
    favorites.value = data.map((item) => item.item)
    console.log(favorites.value)
  } catch (error) {
    console.error(error)
  }
})
</script>

<template>
  <h2 class="text-3xl font-bold mb-8">My bookmarks</h2>

  <CardList :items="favorites" is-favorites />
</template>

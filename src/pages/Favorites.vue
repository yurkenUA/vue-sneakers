<script setup>
import axios from 'axios'
import { onMounted, ref } from 'vue'

import CardList from '../components/CardList.vue'

const apiUrl = import.meta.env.VITE_APP_API_URL

const favorites = ref([])

onMounted(async () => {
  try {
    const { data } = await axios.get(`${apiUrl}/favorites?_relations=items`)
    favorites.value = data.map((item) => item.item)
  } catch (error) {
    console.error(error)
  }
})
</script>

<template>
  <h2 class="text-3xl font-bold mb-8">My bookmarks</h2>

  <CardList :items="favorites" is-favorites />
</template>

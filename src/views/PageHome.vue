<script setup>
import CategoryList from '@/components/CategoryList.vue'
import { useCategoriesStore } from '@/stores/CategoriesStore'
import { storeToRefs } from 'pinia'

const { categories } = storeToRefs(useCategoriesStore())

// const threads = reactive(sourceData.threads)

// function postById (postId) {
//   return posts.find((p) => p.id === postId)
// }
// function userById (userId) {
//   return users.find((p) => p.id === userId)
// }
</script>

<template>
  <h1 class="push-top">Welcome to the Forum</h1>
  <CategoryList :categories="categories" />
</template>

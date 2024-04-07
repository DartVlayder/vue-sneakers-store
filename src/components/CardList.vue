<script setup lang="ts">
import Card from './Card.vue'
import { defineProps, defineEmits } from 'vue'

defineProps<{
  items: Array<{
    id: number
    price: number
    title: string
    imageUrl: string
  }>
}>()
</script>

<template>
  <div class="grid grid-cols-4 gap-5">
    <Card
      v-for="item in items"
      :key="item.id"
      :price="item.price"
      :title="item.title"
      :imageUrl="item.imageUrl"
      clickAdd="onClickAdd"
    />
  </div>
</template>

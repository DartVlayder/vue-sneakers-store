<script setup lang="ts">
import Header from './components/HeaderMain.vue'
import CardList from './components/CardList.vue'
</script>
<template>
  <div class="bg-white w-4/5 m-auto rounded-xl shadow-xl mt-10">
    <Header />
    <div class="p-10">
      <h2 class="text-3xl font-bold mb-8">Все кросовки</h2>
      <CardList />
    </div>
  </div>
</template>

<style scoped></style>

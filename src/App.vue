<script setup lang="ts">
import Header from './components/Header.vue'
import CardList from './components/CardList.vue'
import Drawer from './components/Drawer.vue'
</script>
<template>
  <!-- <Drawer /> -->
  <div class="bg-white w-4/5 m-auto rounded-xl shadow-xl mt-10">
    <Header />
    <div class="p-10">
      <div class="flex justify-between items-center">
        <h2 class="text-3xl font-bold mb-8">Все кросовки</h2>

        <div class="flex gap-4">
          <select class="py-2 px-3 border rounded-mb outline-none">
            <option>По названию</option>
            <option>По цене (дешёвые)</option>
            <option>По цене (дорогие)</option>
          </select>

          <div class="relative">
            <img class="absolute left-3 top-3" src="/search.svg" alt="поиск" />
            <input
              class="border rounded-mb py-2 pl-12 pr-4 outline-none focus:border-gray-400"
              type="text"
              placeholder="Поиск..."
            />
          </div>
        </div>
      </div>
      <CardList />
    </div>
  </div>
</template>

<style scoped></style>
./components/Header.vue

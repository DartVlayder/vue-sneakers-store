<script setup lang="ts">
import { onMounted, reactive, ref, watch } from 'vue'
import axios from 'axios'
import Header from './components/Header.vue'
import CardList from './components/CardList.vue'
import Drawer from './components/Drawer.vue'
const items = ref([])

const filters = reactive({
  sortBy: 'title',
  searchQuery: ''
})

const onChangeSelect = (event) => {
  filters.sortBy = event.target.value
}
const onChangeSearchInput = (event) => {
  filters.searchQuery = event.target.value
}

const fetchItems = async () => {
  try {
    const params = {
      sortBy: filters.sortBy
    }
    if (filters.searchQuery) {
      params.title = `*${filters.searchQuery}*`
    }
    const { data } = await axios.get(`https://f9bd9a56dceb3ac3.mokky.dev/items`, {
      params
    })
    console.log(data)
    items.value = data
  } catch (err) {
    console.log(err)
  }
}

onMounted(fetchItems)
watch(filters, fetchItems)
</script>
<template>
  <!-- <Drawer /> -->
  <div class="bg-white w-4/5 m-auto rounded-xl shadow-xl mt-10">
    <Header />
    <div class="p-10">
      <div class="flex justify-between items-center">
        <h2 class="text-3xl font-bold mb-8">Все кросовки</h2>

        <div class="flex gap-4">
          <select @change="onChangeSelect" class="py-2 px-3 border rounded-mb outline-none">
            <option value="name">По названию</option>
            <option value="price">Сначала дешевле</option>
            <option value="-price">Сначала дороже</option>
          </select>

          <div class="relative">
            <img class="absolute left-3 top-3" src="/search.svg" alt="поиск" />
            <input
              @input="onChangeSearchInput"
              class="border rounded-mb py-2 pl-12 pr-4 outline-none focus:border-gray-400"
              type="text"
              placeholder="Поиск..."
            />
          </div>
        </div>
      </div>
      <div class="mt-10">
        <CardList :items="items" />
      </div>
    </div>
  </div>
</template>

<style scoped></style>
./components/Header.vue

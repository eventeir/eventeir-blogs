<template>
  <div class="p-5 bg-primary-200 text-gray-100 rounded-lg shadow-md">
    <h2 class="text-2xl mb-4">Manage Categories</h2>
    
    <form @submit.prevent="addCategory" class="mb-4">
      <div class="flex items-center w-fit">
        <input
          type="text"
          v-model="newCategory"
          placeholder="Enter category name"
          class="border border-gray-300 rounded-md p-2 w-full mr-2 text-primary-200"
        />
        <button type="submit" class="bg-primary-300 text-gray-100 px-4 py-2 rounded-md">
          Add
        </button>
      </div>
    </form>

    <div>
      <h3 class="text-xl mb-2">Categories</h3>
      <ul class="list-disc pl-5 flex gap-4 flex-wrap">
        <li v-for="(category, index) in categories" :key="index" class="flex items-center justify-between bg-primary-300 px-4 py-2 rounded gap-4">
          <span>{{ category }}</span>
          <button @click="removeCategory(index)" class="text-red-500 hover:text-red-700 h-[24px] w-[24px] rounded-full bg-white hover:bg-gray-200 flex justify-center items-center">
            x
          </button>
        </li>
      </ul>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';

const newCategory = ref('');
const categories = ref<string[]>([]);

const addCategory = () => {
  if (newCategory.value.trim()) {
    categories.value.push(newCategory.value.trim());
    newCategory.value = '';
  }
};

const removeCategory = (index: number) => {
  categories.value.splice(index, 1);
};
</script>

<style scoped>
/* You can add additional styles here if needed */
</style>

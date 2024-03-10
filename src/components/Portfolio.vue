<template>
  <div :id="portfolioId">
    <!-- Filter dropdown -->
    <div class="mb-4">
      <label for="category" class="block text-sm font-medium text-gray-700">Filter by Category:</label>
      <select id="category" v-model="selectedCategory" class="mt-1 block w-full py-2 px-3 border border-gray-300 bg-white rounded-md shadow-sm focus:outline-none focus:ring-blue-500 focus:border-blue-500 sm:text-sm dark:focus:ring-red-500 dark:focus:border-red-500">
        <option value="" class="bg-yellow-700">All</option>
        <option v-for="category in categories" :key="category">{{ category }}</option>
      </select>
    </div>

    <!-- Portfolio cards -->
    <div class="grid md:grid-cols-2 gap-10 mt-16">
      <div v-for="(card, index) in filteredCards" :key="index" class="hover:scale-105 ease-out duration-500 cursor-pointer" @click="toggleVisibility(index)">
        <div class="bg-slate-200 rounded-3xl p-10 h-96">
          <h1 class="text-4xl text-blue-500 dark:text-red-500 font-bold cursor-pointer mb-5">{{ card.title }}</h1>
          <p class="text-lg">{{ card.description }}</p>
        </div>
        <div v-show="visibleDiv === index">
          <!-- Dynamic link -->
          <a :href="card.dynamicLink"><img class="bg-blue-500 dark:bg-red-500 rounded-3xl p-10" :src="card.imageUrl" alt=""></a>
          <p class="text-lg bg-slate-200 rounded-3xl p-10">{{ card.details }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue';
import { portfolioCards } from '../modules/portfolio.js';

// Ref for selected category and visibleDiv
const selectedCategory = ref('');
const visibleDiv = ref(null);

// Toggle visibility function
const toggleVisibility = (index) => {
  visibleDiv.value = visibleDiv.value === index ? null : index;
};

// Computed property for unique categories
const categories = computed(() => {
  const uniqueCategories = new Set();
  portfolioCards.forEach(card => uniqueCategories.add(card.category));
  return Array.from(uniqueCategories);
});

// Computed property for filtered cards based on selected category
const filteredCards = computed(() => {
  if (!selectedCategory.value) return portfolioCards;
  return portfolioCards.filter(card => card.category === selectedCategory.value);
});
</script>

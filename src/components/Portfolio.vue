<template>
  <div :id="portfolioId">
    <h1 class="text-center text-4xl pt-20 pb-10">Showcase</h1>
    <!-- Filter dropdown -->
    <div class="mb-4">
      <label for="category" class="block text-sm font-medium text-gray-700">Filter by Category:</label>
      <select id="category" v-model="selectedCategory" class="mt-1 block w-full py-2 px-3 border border-gray-300 bg-blue-100 dark:bg-red-100 rounded-md shadow-md focus:outline-none focus:ring-blue-500 focus:border-blue-500 sm:text-sm dark:focus:ring-red-500 dark:focus:border-red-500">
        <option value="" class="bg-yellow-700">All</option>
        <option v-for="category in categories" :key="category">{{ category }}</option>
      </select>
    </div>
  </div>

  <!-- Portfolio cards -->
  <div class="grid md:grid-cols-2 gap-10 mt-16">
    <div v-for="(card, index) in filteredCards" :key="index" class="suitcase-card cursor-pointer" @click="toggleVisibility(index)">
      <div class="suitcase-wrapper">
        <div class="suitcase bg-blue-200 dark:bg-red-200 rounded-3xl overflow-hidden border-2 border-blue-300 shadow-xl">
          <div class="suitcase-top bg-blue-400 dark:bg-red-400 p-4 relative">
            <div class="handle bg-blue-600 dark:bg-red-700 w-6 h-2 absolute top-1/2 left-1/2 transform -translate-x-1/2 -translate-y-1/2"></div>
          </div>
          <div class="suitcase-body hover:bg-blue-300 dark:hover:bg-red-300 ease-out duration-500 bg-blue-200 h-80 xl:h-64 dark:bg-red-200 p-4">
            <h1 class="text-4xl text-gray-800 font-bold cursor-pointer mb-5 px-10">{{ card.title }}</h1>
            <p class="text-lg 2xl:px-10">{{ card.description }}</p>
          </div>
          <div v-show="visibleDiv === index">
            <a @click="openModalWithWebsite(card.dynamicLink)">
              <img class="bg-blue-200 blur-[2px] hover:blur-0  dark:bg-red-200 ease-in-out duration-1000" :src="card.imageUrl" alt="">
            </a>
            <p class="text-lg bg-blue-200 dark:bg-red-200 p-10">{{ card.details }}</p>
          </div>
        </div>
      </div>
    </div>
  </div>

  <!-- Modal component -->
  <WebsiteModal v-if="showModal" :websiteUrl="modalWebsiteUrl" @closeModal="showModal = false" />

</template>

<script setup>
import { ref, computed } from 'vue';
import { portfolioCards } from '../modules/portfolio.js';
import WebsiteModal from './Modal.vue';

const portfolioId = 'portfolio';

// Define reactive variables
const selectedCategory = ref('');
const visibleDiv = ref(null);
const showModal = ref(false);
const modalWebsiteUrl = ref('');

// Function to toggle visibility
const toggleVisibility = (index) => {
  visibleDiv.value = visibleDiv.value === index ? null : index;
};

// Function to open modal with website URL
const openModalWithWebsite = (url) => {
  modalWebsiteUrl.value = url;
  showModal.value = true;
};

// Compute unique categories
const categories = computed(() => {
  const uniqueCategories = new Set();
  portfolioCards.forEach(card => uniqueCategories.add(card.category));
  return Array.from(uniqueCategories);
});

// Compute filtered cards based on selected category
const filteredCards = computed(() => {
  if (!selectedCategory.value) return portfolioCards;
  return portfolioCards.filter(card => card.category === selectedCategory.value);
});

</script>

<style>
/* Add your custom styles here */
</style>

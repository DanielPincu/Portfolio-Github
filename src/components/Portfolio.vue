<template>
  <div class="border-t-2 border-b-2 pb-20 border-zinc-200 pt-20" id="portfolio">
    <div 
     data-aos="flip-right"
     data-aos-easing="ease-in-back"
     data-aos-duration="800"
     >
    

      <h1 class="text-center text-4xl pb-10">Showcase</h1>
      <!-- Filter dropdown -->
      <div class="mb-4">
        <label for="category" class="block text-sm font-medium text-gray-700">Filter by Category:</label>
        <select id="category"
                v-model="selectedCategory"
                class="mt-1 block w-full py-2 px-3 border border-gray-300 bg-blue-100 dark:bg-red-100 rounded-md shadow-md focus:outline-none focus:ring-blue-500 focus:border-blue-500 sm:text-sm dark:focus:ring-red-500 dark:focus:border-red-500">
          <option value="" class="bg-yellow-700">All</option>
          <option v-for="category in categories" :key="category">{{ category }}</option>
        </select>
      </div>
    </div>

    <!-- Portfolio cards -->
    <div class="grid md:grid-cols-2 gap-10 mt-16">
    
    
      <div v-for="(card, index) in filteredCards" :key="index" class="suitcase-card cursor-pointer" @click="toggleVisibility(index)" 
     data-aos="zoom-in"
     data-aos-easing="ease-out-back"
     data-aos-duration="1000"
      >
        <div class="suitcase-wrapper">
          <div class="suitcase bg-blue-200 dark:bg-red-200 rounded-3xl overflow-hidden border-2 border-blue-300 dark:border-red-300 shadow-xl">
            <div class="suitcase-top bg-blue-400 dark:bg-red-400 p-4 relative">
              <div class="handle bg-blue-600 dark:bg-red-700 w-6 h-2 absolute top-1/2 left-1/2 transform -translate-x-1/2 -translate-y-1/2"></div>
            </div>
            <div class="suitcase-body hover:bg-blue-300 dark:hover:bg-red-300 ease-out duration-500 bg-blue-200 h-60 dark:bg-red-200 p-4">
              <h1 class="text-4xl text-gray-800 font-bold cursor-pointer mb-5 2xl:pl-5">{{ card.title }}</h1>
              <p class=" mb-5 2xl:px-5">{{ card.description }}</p>
            </div>
            <div v-show="visibleDiv === index">
              <a @click="openWebsite(card.dynamicLink)">
                <img class="bg-blue-200 border-t-2 border-b-2 border-transparent hover:border-blue-500 hover:dark:border-red-500 dark:bg-red-200 ease-in-out duration-100"
                     :src="card.imageUrl" alt="">
              </a>
              <p class="bg-blue-200 dark:bg-red-200 p-10">{{ card.details }}</p>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- Modal component -->
    <div class="fixed inset-0 overflow-y-auto z-10" v-if="showModal">
      <div class="flex items-center justify-center min-h-screen pt-4 px-4 pb-20 text-center">
        <div class="fixed inset-0 transition-opacity" aria-hidden="true">
          <div class="absolute inset-0 bg-gray-500 opacity-75"></div>
        </div>
        <span class="hidden sm:inline-block sm:align-middle sm:h-screen" aria-hidden="true">&#8203;</span>
        <div class="inline-block bg-white rounded-3xl text-left overflow-hidden shadow-xl transform transition-all my-8 align-middle w-[1200px]">
          <div class="bg-white px-4 pt-5 pb-4">
            <iframe :src="websiteUrl" frameborder="0" allowfullscreen class="w-full h-[70vh]"></iframe>
          </div>
          <div class="bg-gray-50 px-4 py-3 flex flex-row-reverse">
            <button @click="showModal = false" type="button" class="my-5 inline-flex justify-center w-full rounded-full px-4 py-2 bg-gradient-to-r from-blue-400 to-blue-600 dark:from-red-400 dark:to-red-600 font-medium text-white shadow-sm hover:bg-red-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-red-500 ml-3 text-sm">
              Close
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue';
import { portfolioCards } from '../modules/portfolio.js';

//  reactive variables
const selectedCategory = ref('');
const visibleDiv = ref(null);
const showModal = ref(false);
const websiteUrl = ref('');

// o toggle visibility
const toggleVisibility = (index) => {
  visibleDiv.value = visibleDiv.value === index ? null : index;
};

//  open modal with website url
const openWebsite = (url) => {
  websiteUrl.value = url;
  showModal.value = true;
};

// Calculate unique categories
  const categories = computed(() => {
  const uniqueCategories = new Set();
  portfolioCards.forEach(card => uniqueCategories.add(card.category));
  return Array.from(uniqueCategories);
});

//  filtered cards based on selected category
const filteredCards = computed(() => {
  if (!selectedCategory.value) return portfolioCards;
  return portfolioCards.filter(card => card.category === selectedCategory.value);
});

</script>

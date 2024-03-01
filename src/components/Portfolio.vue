<template>
  <div id="portfolio">
    <div class="mb-4">
      <label for="category" class="block text-sm font-medium text-gray-700">Filter by Category:</label>
      <select id="category" v-model="selectedCategory" class="mt-1 block w-full py-2 px-3 border border-gray-300 bg-white rounded-md shadow-sm focus:outline-none focus:ring-yellow-500 focus:border-yellow-500 sm:text-sm">
        <option value="" class="bg-yellow-700">All</option>
        <option v-for="category in categories" :key="category">{{ category }}</option>
      </select>
    </div>

    <div class="grid md:grid-cols-2 gap-10 mt-16">
      <div v-for="(card, index) in filteredCards" :key="index" class="hover:scale-105 ease-out duration-500 cursor-pointer" @click="toggleVisibility(index)">
        <div class="bg-yellow-400 rounded-3xl p-10 h-80">
          <h1 class="text-4xl font-bold cursor-pointer mb-5">{{ card.title }}</h1>
          <p class="text-xl">{{ card.description }}</p>
        </div>
        <div v-show="visibleDiv === index">
          <a :href="card.imageUrl"><img class="bg-yellow-400 rounded-3xl p-10" :src="card.imageUrl" alt=""></a>
          <p class="text-xl bg-yellow-400 rounded-3xl p-10">{{ card.details }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue';

const cards = ref([
  {
    title: 'Trapholt',
    description: "I'm proud to present a project where I contributed and executed a comprehensive redesign for Trapholt Museum, renowned cultural institution in Kolding, Denmark",
    category: 'Web Design',
    imageUrl: 'src/assets/img/trap1.png',
    details: 'The website features intuitive navigation, immersive imagery, and interactive elements to enhance the user experience. Additionally, I integrated functionalities such as event listings, virtual tours, and online ticketing to streamline visitor engagement and accessibility'
  },

  {
    title: 'Chatognito',
    description: "I'm proud to present a project where I contributed and executed a comprehensive redesign for Trapholt Museum, renowned cultural institution in Kolding, Denmark",
    category: 'Design',
    imageUrl: 'src/assets/img/trap1.png',
    details: 'The website features intuitive navigation, immersive imagery, and interactive elements to enhance the user experience. Additionally, I integrated functionalities such as event listings, virtual tours, and online ticketing to streamline visitor engagement and accessibility'
  },

  {
    title: 'InDesign',
    description: "I'm proud to present a project where I contributed and executed a comprehensive redesign for Trapholt Museum, renowned cultural institution in Kolding, Denmark",
    category: 'Art', 
    imageUrl: 'src/assets/img/trap1.png',
    details: 'The website features intuitive navigation, immersive imagery, and interactive elements to enhance the user experience. Additionally, I integrated functionalities such as event listings, virtual tours, and online ticketing to streamline visitor engagement and accessibility'
  },

  {
    title: 'InDesign',
    description: "I'm proud to present a project where I contributed and executed a comprehensive redesign for Trapholt Museum, renowned cultural institution in Kolding, Denmark",
    category: 'Art', 
    imageUrl: 'src/assets/img/trap1.png',
    details: 'The website features intuitive navigation, immersive imagery, and interactive elements to enhance the user experience. Additionally, I integrated functionalities such as event listings, virtual tours, and online ticketing to streamline visitor engagement and accessibility'
  },
  {
    title: 'InDesign',
    description: "I'm proud to present a project where I contributed and executed a comprehensive redesign for Trapholt Museum, renowned cultural institution in Kolding, Denmark",
    category: 'Art', 
    imageUrl: 'src/assets/img/trap1.png',
    details: 'The website features intuitive navigation, immersive imagery, and interactive elements to enhance the user experience. Additionally, I integrated functionalities such as event listings, virtual tours, and online ticketing to streamline visitor engagement and accessibility'
  },
  {
    title: 'InDesign',
    description: "I'm proud to present a project where I contributed and executed a comprehensive redesign for Trapholt Museum, renowned cultural institution in Kolding, Denmark",
    category: 'Art', 
    imageUrl: 'src/assets/img/trap1.png',
    details: 'The website features intuitive navigation, immersive imagery, and interactive elements to enhance the user experience. Additionally, I integrated functionalities such as event listings, virtual tours, and online ticketing to streamline visitor engagement and accessibility'
  },


  
  // Add more card objects as needed
]);

const categories = computed(() => {
  const uniqueCategories = new Set();
  cards.value.forEach(card => uniqueCategories.add(card.category));
  return Array.from(uniqueCategories);
});

const selectedCategory = ref('');
const visibleDiv = ref(null);

const toggleVisibility = (index) => {
  visibleDiv.value = visibleDiv.value === index ? null : index;
};

const filteredCards = computed(() => {
  if (!selectedCategory.value) return cards.value;
  return cards.value.filter(card => card.category === selectedCategory.value);
});
</script>

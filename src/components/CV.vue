<template>
  <div id="home">
    <!-- Profile Info -->
    <div>
      <div class="flex justify-center">
        <img class="w-48 mt-10" :src="profile.image" :alt="profile.name">
      </div>
      <div class="border-b-2 border-zinc-200 pb-5">
        <h1 class="text-2xl font-bold text-center mt-5">{{ profile.name }}</h1>
        <p class="text-center text-gray-500">{{ profile.title }}</p>
        
      </div>
      <!-- Additional sections -->
      <div v-for="(additionalSection, index) in additionalSections" :key="'additionalSection' + index" class="shadow-xl border-2 border-blue-300 dark:border-red-300 mx-5 mt-5 flex flex-col bg-blue-200 dark:bg-red-200 rounded-full items-center justify-end h-16">
        <h1 class="text-xl font-bold">{{ additionalSection.title }}</h1>
        <p class="text-xl">{{ additionalSection.content }}</p>
      </div>
     
    </div>

    <!-- Dynamic Sections -->
    <div v-for="(section, index) in dynamicSections" :key="index" class="pt-10">
      <h1 class="font-bold text-2xl text-center pt-5">{{ section.title }}</h1>
      <div v-for="(item, idx) in section.items" :key="idx" class="shadow-xl border-2 border-blue-300 dark:border-red-300 mx-5 my-5 flex flex-col bg-blue-200 dark:bg-red-200 rounded-full items-center h-16 justify-center">
        <h1 class="text-xl font-bold px-4">{{ item.name }}</h1>
        <div class="w-36 xl:w-56 2xl:w-64 bg-blue-300 dark:bg-red-300 rounded-full">
          <div class="bg-blue-500 dark:bg-red-500 text-xs font-bold text-center text-white p-1 leading-none rounded-full" :style="{ width: item.percentage }">{{ item.percentage }}</div>
        </div>
      </div>
    </div>
  </div>
  
</template>

<script setup>
import { ref, onMounted } from 'vue';
import anime from 'animejs';
import { profileData, additionalSectionsData, dynamicSectionsData } from '../modules/cv';

const profile = ref(profileData);
const additionalSections = ref(additionalSectionsData);
const dynamicSections = ref(dynamicSectionsData);

onMounted(() => {
  anime({
    targets: '.tt',
    opacity: [0, 1],
    translateY: [-500, 0],
    translateX: [400, 0], 
    easing: "linear",
    duration: 3000,
  });
});
</script>



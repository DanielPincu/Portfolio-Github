<template>  
  <div class="flex justify-center md:pt-10 pt-0">
    <h1 class="text-4xl pt-16 pb-16">Services</h1>
  </div>

  <div class="grid md:grid-cols-4 grid-cols-2 items-center gap-5 md:pb-10 mb-16">
    <div v-for="(service, index) in services" :key="index" @click="toggleVisibility(index)" :class="service.wrapperClasses">
      <h1 class="text-2xl text-center pt-10">{{ service.title }}</h1>
      <svg :class="service.svgClasses" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor">
        <path stroke-linecap="round" stroke-linejoin="round" :d="service.svgPath" />
      </svg>
      <div v-show="visibleDiv === index" class="animate-bounce bg-yellow-100 rounded-3xl drop-shadow-xl h-60 flex flex-col items-center mb-2 w-full">
        <h1 class="text-xl p-5">{{ service.description }}</h1>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const services = ref([
  {
    title: 'Web Dev',
    wrapperClasses: 'bg-yellow-500 rounded-3xl drop-shadow-xl h-60 flex flex-col items-center mb-10 hover:scale-[103%] duration-500',
    svgClasses: 'w-32 md:w-64 justify-center',
    svgPath: 'M9 17.25v1.007a3 3 0 0 1-.879 2.122L7.5 21h9l-.621-.621A3 3 0 0 1 15 18.257V17.25m6-12V15a2.25 2.25 0 0 1-2.25 2.25H5.25A2.25 2.25 0 0 1 3 15V5.25m18 0A2.25 2.25 0 0 0 18.75 3H5.25A2.25 2.25 0 0 0 3 5.25m18 0V12a2.25 2.25 0 0 1-2.25 2.25H5.25A2.25 2.25 0 0 1 3 12V5.25',
    description: 'Looking for a website for your company?'
  },
  {
    title: 'Graphic',
    wrapperClasses: 'bg-yellow-500 rounded-3xl drop-shadow-xl h-60 flex flex-col items-center mb-10 hover:scale-[103%] duration-500',
    svgClasses: 'w-32 md:w-64',
    svgPath: 'm2.25 15.75 5.159-5.159a2.25 2.25 0 0 1 3.182 0l5.159 5.159m-1.5-1.5 1.409-1.409a2.25 2.25 0 0 1 3.182 0l2.909 2.909m-18 3.75h16.5a1.5 1.5 0 0 0 1.5-1.5V6a1.5 1.5 0 0 0-1.5-1.5H3.75A1.5 1.5 0 0 0 2.25 6v12a1.5 1.5 0 0 0 1.5 1.5Zm10.5-11.25h.008v.008h-.008V8.25Zm.375 0a.375.375 0 1 1-.75 0 .375.375 0 0 1 .75 0Z',
    description: 'Do you need a new look for website?'
  },
  {
    title: 'Video edit',
    wrapperClasses: 'bg-yellow-500 rounded-3xl drop-shadow-xl h-60 flex flex-col items-center mb-10 hover:scale-[103%] duration-500',
    svgClasses: 'w-32 md:w-64',
    svgPath: 'm15.75 10.5 4.72-4.72a.75.75 0 0 1 1.28.53v11.38a.75.75 0 0 1-1.28.53l-4.72-4.72M4.5 18.75h9a2.25 2.25 0 0 0 2.25-2.25v-9a2.25 2.25 0 0 0-2.25-2.25h-9A2.25 2.25 0 0 0 2.25 7.5v9a2.25 2.25 0 0 0 2.25 2.25Z',
    description: 'Need professional video editing?'
  },
  {
    title: 'UI / UX',
    wrapperClasses: 'bg-yellow-500 rounded-3xl drop-shadow-xl h-60 mb-10 flex flex-col items-center hover:scale-[103%] duration-500',
    svgClasses: 'w-32 md:w-64',
    svgPath: 'M3.75 3.75v4.5m0-4.5h4.5m-4.5 0L9 9M3.75 20.25v-4.5m0 4.5h4.5m-4.5 0L9 15M20.25 3.75h-4.5m4.5 0v4.5m0-4.5L15 9m5.25 11.25h-4.5m4.5 0v-4.5m0 4.5L15 15',
    description: 'Looking for intuitive design solutions?'
  }
]);

const visibleDiv = ref(null);

const toggleVisibility = (index) => {
  visibleDiv.value = visibleDiv.value === index ? null : index;
};
</script>


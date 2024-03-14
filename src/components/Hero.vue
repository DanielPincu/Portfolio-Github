<template>
  <div class="lg:hidden sticky top-0 z-10 bg-blue-500 text-white dark:bg-red-500 -mx-5">
    <div class="flex justify-between items-center mt-10 mx-5 sticky top-20">
      <div class="flex my-5">
        <div v-for="(navItem, index) in navItems" :key="index" class="mx-3">
          <a @click="scrollTo(navItem.href, $event)" class="text-lg font-bold cursor-pointer hover:scale-110 hover:transition ease-in-out duration-700">{{ navItem.label }}</a>
        </div>
      </div>
      <label class="inline-flex items-center cursor-pointer">
        <input type="checkbox" value="" class="sr-only peer" v-model="isDark">
        <div class="relative w-11 h-6 bg-red-700 rounded-full peer dark:bg-red-600 peer-checked:after:translate-x-full rtl:peer-checked:after:-translate-x-full peer-checked:after:border-white after:content-[''] after:absolute after:top-[2px] after:start-[2px] after:bg-white after:border-gray-300 after:border after:rounded-full after:h-5 after:w-5 after:transition-all dark:border-gray-600 peer-checked:bg-blue-600"></div>
      </label>
    </div>
  </div>

  <div class="relative">

  <img class="rounded-full border-4 border-blue-500 dark:border-red-500 mx-auto w-[90%] m-10 dark:scale-x-[-1]" src="../assets/img/matrix.jpeg" alt="">
  


  <div class="absolute inset-0 flex flex-col justify-center items-center text-center">
    <h1 class="text-sm md:text-xl pb-10 xl:text-3xl font-bold text-white">
      I’m Daniel Pincu <br> <span class="text-blue-500 dark:text-red-500">Front-end</span> Developer
    </h1>
    <p class="text-xl md:text-3xl xl:text-5xl mb-1  text-white">Welcome to the Matrix<span class="animate-pulse animate-fast">|</span>
</p>
   <div class="flex md:pt-5 2xl:pt-24">
    <a href="./src/assets/img/cv.pdf">
  <button class="hidden dark:block cv-button bg-gradient-to-r from-blue-400 to-blue-600 dark:from-red-400 dark:to-red-600 shadow-lg border-b-2 border-slate-50 text-white font-bold text-sm md:text-xl px-5 md:py-6 2xl:px-0 rounded-full w-38 md:w-44 mr-10 md:mr-44 2xl:mr-64">Fetch CV</button>
</a>

<a href="src/assets/img/videocv.mp4">
  <button class="block dark:hidden cv-button bg-gradient-to-r from-blue-400 to-blue-600 dark:from-red-400 dark:to-red-600 shadow-lg border-b-2 border-slate-50 text-white font-bold text-sm md:text-xl px-5 md:py-6 2xl:px-0 rounded-full w-38 md:w-44 mr-10 md:mr-44 2xl:mr-64">Watch CV</button>

  <a href="src/assets/img/videocv.mp4">
  <button class="hidden dark:block cv-button bg-gradient-to-r from-blue-400 to-blue-600 dark:from-blue-400 dark:to-blue-600 shadow-lg border-b-2 border-slate-50 text-white font-bold text-sm md:text-xl px-5 md:py-6 2xl:px-0 rounded-full w-38 md:w-44">Watch CV</button>
</a>

<a href="src/assets/img/cv.pdf">
  <button class="block dark:hidden cv-button bg-gradient-to-r from-red-400 to-red-600 dark:from-red-400 dark:to-red-600 shadow-lg border-b-2 border-slate-50 text-white font-bold text-sm md:text-xl px-5 md:py-6 2xl:px-0 rounded-full w-38 md:w-44">Fetch CV</button>
</a>


</a>

</div>

  </div>
</div>


  
</template>

<script setup>
// import { ref } from 'vue';
// const buttons = ref([
//   { text: 'Discover more', target: '#portfolio' },
// ]);

import { navItems } from '../modules/nav'; // Importing external navigation data

const scrollToElement = (target) => {
  const element = document.querySelector(target);
  if (element) {
    const offsetTop = element.offsetTop;
    window.scrollTo({
      top: offsetTop,
      behavior: "smooth"
    });
  }
};

import { useDark, useToggle } from "@vueuse/core";

const isDark = useDark();
const toggleDark = useToggle(isDark);

const scrollTo = (target, event) => {
  event.preventDefault();
  const element = document.querySelector(target);
  if (element) {
    const offsetTop = element.offsetTop;
    window.scrollTo({
      top: offsetTop,
      behavior: "smooth"
    });
  }
};
</script>

<style>
  @keyframes pulse {
    0%, 100% {
      opacity: 1;
    }
    50% {
      opacity: 0.1;
    }
  }
  
  .animate-pulse {
    animation: pulse 1s cubic-bezier(0.4, 0, 0.6, 1) infinite;
  }
  
  .animate-fast {
    animation-duration: 0.3s;
  }
</style>
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

  <!-- <div class="h-[700px] lg:grid grid-cols-2 items-center pb-0 md:pb-20 xl:border-blue-900 xl:dark:border-red-900 xl:border-4 xl:rounded-full mt-20 pl-[45px] lg:pl-24 pt-20 pr-5 mr-5 bg-[url('src/assets/img/matrix.jpeg')] bg-cover">
   
    <div class="flex flex-col">
      <h1 class="text-xl font-bold ml-0 xl:text-white">
        I’m Daniel Pincu <br> <span class="text-blue-500 dark:text-red-500">Front-end</span> Developer
      </h1>
      <p class="text-3xl mt-5 font-medium xl:text-white">Welcome to the Matrix</p>
      <a v-for="(button, index) in buttons" :key="index" :href="button.target" @click.prevent="scrollToElement(button.target)">
        <div class="text-xl bg-blue-500 mt-10 p-5  ml-0 w-30 rounded-full text-center text-white hover:text-blue-900 transition-all duration-400 dark:bg-red-500">{{ button.text }}</div>
      </a>
    </div>
   
    <div class="flex justify-center">
      <img class="rounded-full w-96 p-10" src="https://images.unsplash.com/photo-1521119989659-a83eee488004?q=80&w=2823&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D" alt="Daniel Pincu">
    </div> 
    
  </div> -->

  <div class="relative">

  <img class="rounded-full border-4 border-blue-500 dark:border-red-500 mx-auto w-[90%] m-10 dark:scale-x-[-1]" src="../assets/img/matrix.jpeg" alt="">
  


  <div class="absolute inset-0 flex flex-col justify-center items-center text-center">
    <h1 class="text-sm md:text-xl pb-10 xl:text-3xl font-bold text-white">
      I’m Daniel Pincu <br> <span class="text-blue-500 dark:text-red-500">Front-end</span> Developer
    </h1>
    <p class="text-xl md:text-3xl xl:text-5xl mb-1  text-white">Welcome to the Matrix<span class="animate-pulse animate-fast">|</span>
</p>
   <div class="flex md:pt-5 2xl:pt-24">
  <button class="hidden dark:block bg-gradient-to-r from-blue-400 to-blue-600 dark:from-red-400 dark:to-red-600 shadow-lg border-b-2 border-slate-50 text-white font-bold text-sm md:text-xl px-5 md:py-6 2xl:px-0 rounded-full w-38 md:w-44 mr-10 md:mr-44 2xl:mr-64">Fetch CV</button>

  <button class="block dark:hidden bg-gradient-to-r from-blue-400 to-blue-600 dark:from-red-400 dark:to-red-600 shadow-lg border-b-2 border-slate-50 text-white font-bold text-sm md:text-xl px-5 md:py-6 2xl:px-0 rounded-full w-38 md:w-44 mr-10 md:mr-44 2xl:mr-64">Watch CV</button>

  <button class="hidden dark:block bg-gradient-to-r from-red-400 to-red-600 dark:from-blue-400 dark:to-blue-600 shadow-lg border-b-2 border-slate-50 text-white font-bold text-sm md:text-xl px-5 2xl:px-0 py-2 rounded-full w-38 md:w-44">Watch CV</button>
  
  <button class="block dark:hidden bg-gradient-to-r from-red-400 to-red-600 dark:from-blue-400 dark:to-blue-600 shadow-lg border-b-2 border-slate-50 text-white font-bold text-sm md:text-xl px-5 2xl:px-0 py-2 rounded-full w-38 md:w-44">Fetch CV</button>
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
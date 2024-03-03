<template>


<label  class="inline-flex items-center cursor-pointer mt-20 ml-10 sticky top-[100px]">
  <input type="checkbox" value="" class="sr-only peer">
  <div @click="toggleDark()" class="relative w-11 h-6 bg-red-700 peer-focus:outline-none peer-focus:ring-4 peer-focus:ring-blue-300 dark:peer-focus:ring-blue-800 rounded-full peer dark:bg-red-600 peer-checked:after:translate-x-full rtl:peer-checked:after:-translate-x-full peer-checked:after:border-white after:content-[''] after:absolute after:top-[2px] after:start-[2px] after:bg-white after:border-gray-300 after:border after:rounded-full after:h-5 after:w-5 after:transition-all dark:border-gray-600 peer-checked:bg-blue-600"></div>
  
</label>

  <div class="mt-10 sticky top-[300px] mx-5 mr-5">
    <div class="flex justify-evenly items-center rounded-full">
      <a class="text-lg font-bold text-blue-900 cursor-pointer hover:scale-110 hover:transition ease-in-out duration-700" @click="scrollTo('#home')">Home</a>
    </div>

    <div class="flex justify-evenly items-center my-5">
      <a class="text-lg font-bold text-blue-900 cursor-pointer hover:scale-110 hover:transition ease-in-out duration-700" @click="scrollTo('#portfolio')">Portfolio</a>
    </div>

    <div class="flex justify-evenly items-center my-5">
      <a class="text-lg font-bold text-blue-900 cursor-pointer hover:scale-110 hover:transition ease-in-out duration-700" @click="scrollTo('#about')">About</a>
    </div>

    <div class="flex justify-evenly items-center my-5">
      <a class="text-lg font-bold text-blue-900 cursor-pointer hover:scale-110 hover:transition ease-in-out duration-700" @click="scrollTo('#contact')">Contact</a>
    </div>
  </div>
</template>

<script setup>

const scrollTo = (target) => {
  const element = document.querySelector(target);
  if (element) {
    const offsetTop = element.offsetTop;
    window.scrollTo({
      top: offsetTop,
      behavior: "smooth"
    });
  }
};

import {useDark, useToggle}  from "@vueuse/core"



    const isDark = useDark()  
    const toggleDark = useToggle(isDark)
    

</script>
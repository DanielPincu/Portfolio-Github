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

  <div class="lg:grid grid-cols-2 items-center pb-0 md:pb-20 xl:border-black xl:border-2 xl:rounded-full mt-20 pl-[45px] lg:pl-24 pt-20 pr-5 mr-5">
    <!-- intro start -->
    <div class="flex flex-col">
      <h1 class="text-xl font-bold ml-0">
        I’m Daniel Pincu <br> <span class="text-blue-500 dark:text-red-500">Front-end</span> Developer
      </h1>
      <p class="text-lg mt-5 font-medium">Designing and coding beautifully simple things requires a blend of creativity, technical skill, and attention to detail. It's a craft that involves finding elegant solutions to complex problems, all while keeping the end user in mind.</p>
      <a v-for="(button, index) in buttons" :key="index" :href="button.target" @click.prevent="scrollToElement(button.target)">
        <div class="text-xl bg-blue-500 mt-10 p-5  ml-0 w-30 rounded-full text-center text-white hover:text-blue-900 transition-all duration-400 dark:bg-red-500">{{ button.text }}</div>
      </a>
    </div>
    <!-- intro ends -->

    <!-- image start -->
    <div class="flex justify-center ">
      <img class="rounded-full w-96 p-10" src="https://images.unsplash.com/photo-1521119989659-a83eee488004?q=80&w=2823&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D" alt="Daniel Pincu">
    </div>
    <!-- image ends -->
  </div>
</template>

<script setup>
import { ref } from 'vue';

const buttons = ref([
  { text: 'Discover more', target: '#portfolio' },
  
]);

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

const navItems = [
  { label: "Home", href: "#home" },
  { label: "Portfolio", href: "#portfolio" },
  { label: "About", href: "#about" },
  { label: "Contact", href: "#contact" }
]

import {useDark, useToggle}  from "@vueuse/core"



    const isDark = useDark()  
    const toggleDark = useToggle(isDark)


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

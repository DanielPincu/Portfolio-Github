<template>
   <div class="lg:hidden sticky top-0 z-10 bg-yellow-300 -mx-5">

    


      <div class="mt-10 flex justify-center">

        <div class="flex items-center my-5 px-5">

         <h1 class="text-lg font-bold text-blue-900">Home</h1>
          
      
        </div>
      
        
          <div class="flex items-center  my-5 px-5">
            
            
            <h1 class="text-lg font-bold text-blue-900">Portfolio</h1>
            
        
          </div>


          <div class="flex items-center  my-5 px-5">
            
            <h1 class="text-lg font-bold text-blue-900">About</h1>
            
        
          </div>
        
          <div class="flex items-center  my-5 px-5">
            
            <h1 class="text-lg font-bold text-blue-900">Contact</h1>
            
        
          </div>
        
      </div>
    </div>

  <div class="lg:grid grid-cols-2 items-center pb-0 md:pb-20 xl:border-black xl:border-2 xl:rounded-full mt-20 pl-24 pt-20 pr-5 mr-5">
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


import {useDark, useToggle}  from "@vueuse/core"



    const isDark = useDark()  
    const toggleDark = useToggle(isDark)
    
</script>

<!-- YourComponent.vue -->
<template>
  <div class="lg:hidden sticky top-0 z-10 bg-blue-100 dark:bg-red-100 -mx-5">
    <!-- Navigation Bar -->
    <div class="flex justify-center items-center mt-10 sticky top-20">
      <div class="flex my-5">
        <div v-for="(navItem, index) in navItems" :key="index" class="mx-3">
          <a @click="scrollTo(navItem.href, $event)" class="text-lg font-bold cursor-pointer hover:scale-110 hover:transition ease-in-out duration-700">{{ navItem.label }}</a>
        </div>
      </div>
    </div>
  </div>

  <div class="relative">
    <!-- Profile Image -->
    <img class="rounded-full border-4 border-blue-500 dark:border-red-500 mx-auto w-[90%] m-10 dark:scale-x-[-1]" :src="profileImageSrc" alt="">

    <!-- Welcome Message -->
    <div class="absolute inset-0 flex flex-col justify-center items-center text-center">
      <h1 class="text-sm md:text-xl pb-10 xl:text-3xl font-bold text-white">
        {{ welcomeMessage.name }} <br>
        <span class="text-blue-500 dark:text-red-500">{{ welcomeMessage.role }}</span>
      </h1>

      <!-- Dark Mode Toggle -->
      <label class="inline-flex items-center lg:hidden cursor-pointer">
        <input type="checkbox" value="" class="sr-only peer" v-model="isDark">
        <!-- Dark Mode Switch -->
        <div class="relative w-11 h-6 bg-red-700 rounded-full peer dark:bg-red-600 peer-checked:after:translate-x-full rtl:peer-checked:after:-translate-x-full peer-checked:after:border-white after:content-[''] after:absolute after:top-[2px] after:start-[2px] after:bg-white after:border-gray-300 after:border after:rounded-full after:h-5 after:w-5 after:transition-all dark:border-gray-600 peer-checked:bg-blue-600"></div>
      </label>

      <!-- Welcome Text -->
      <p class="text-xl md:text-3xl xl:text-5xl pl-3 mb-1 text-white">{{ welcomeText }}</p>

      <!-- CV Buttons -->
      <div class="flex md:pt-5 2xl:pt-24">
        <a :href="cvFetchLink">
          <button class="hidden dark:block cv-button bg-gradient-to-r from-blue-400 to-blue-600 dark:from-red-400 dark:to-red-600 shadow-lg border-b-2 border-slate-50 text-white font-bold text-sm md:text-xl px-5 md:py-6 2xl:px-0 rounded-full w-38 md:w-44 mr-2 md:mr-44 2xl:mr-64">{{ cvFetchText }}</button>
        </a>
        <a :href="cvWatchLink">
          <button class="block dark:hidden cv-button bg-gradient-to-r from-blue-400 to-blue-600 dark:from-red-400 dark:to-red-600 shadow-lg border-b-2 border-slate-50 text-white font-bold text-sm md:text-xl px-5 md:py-6 2xl:px-0 rounded-full w-38 md:w-44 mr-2 md:mr-44 2xl:mr-64">{{ cvWatchText }}</button>
        </a>
        <a :href="cvWatchLink">
          <button class="hidden dark:block cv-button bg-gradient-to-r from-blue-400 to-blue-600 dark:from-blue-400 dark:to-blue-600 shadow-lg border-b-2 border-slate-50 text-white font-bold text-sm md:text-xl px-5 md:py-6 2xl:px-0 rounded-full w-38 md:w-44">{{ cvWatchText }}</button>
        </a>
        <a :href="cvFetchLink">
          <button class="block dark:hidden cv-button bg-gradient-to-r from-red-400 to-red-600 dark:from-red-400 dark:to-red-600 shadow-lg border-b-2 border-slate-50 text-white font-bold text-sm md:text-xl px-5 md:py-6 2xl:px-0 rounded-full w-38 md:w-44">{{ cvFetchText }}</button>
        </a>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import { navItems } from '../modules/nav';
import { profileImageSrc, welcomeMessage, welcomeText, cvFetchLink, cvFetchText, cvWatchLink, cvWatchText } from '../modules/hero';

// Dark Mode Toggle
import { useDark } from "@vueuse/core";
const isDark = useDark();

// Scroll To Function
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
/* Your component styles here */
</style>

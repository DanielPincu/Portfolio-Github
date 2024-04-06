<template>
  
    <!-- Mobile Navigation Bar -->
    <div class="lg:hidden sticky top-0 z-10 bg-blue-100 dark:bg-red-100 -mx-5">
      <div class="flex justify-center items-center mt-10">
        <div class="flex my-5">
          <div v-for="(navItem, index) in navItems" :key="index" class="mx-3">
            <a @click="scrollTo(navItem.href, $event)" class="text-lg font-bold cursor-pointer hover:scale-110 hover:transition ease-in-out duration-700">{{ navItem.label }}</a>
          </div>
        </div>
      </div>
    </div>

    <div class="relative" 
    data-aos="flip-right"
    data-aos-duration="1000">


      <!-- Profile Image -->
      <img class="rounded-full blink border-blue-500 dark:border-red-500 mx-auto w-[90%] m-10 dark:scale-x-[-1]" :src="profileImageSrc" alt="">

      <!-- Welcome Message -->
      <div class="absolute inset-0 flex flex-col justify-center items-center text-center">
        <h1 class="text-sm md:text-xl pb-10 xl:text-3xl font-bold text-white">
          {{ welcomeMessage.name }} <br>
          <span class="text-blue-500 dark:text-red-500">{{ welcomeMessage.role }}</span>
        </h1>

        <!-- Dark Mode Toggle -->
        <label class="inline-flex items-center lg:hidden cursor-pointer">
          <input type="checkbox" value="" class="sr-only peer" v-model="isDark">
          <div class="relative w-11 h-6 bg-red-700 rounded-full peer dark:bg-red-600 peer-checked:after:translate-x-full rtl:peer-checked:after:-translate-x-full peer-checked:after:border-white after:content-[''] after:absolute after:top-[2px] after:start-[2px] after:bg-white after:border-gray-300 after:border after:rounded-full after:h-5 after:w-5 after:transition-all dark:border-gray-600 peer-checked:bg-blue-600"></div>
        </label>

        <!-- Welcome Text -->
        <p class="text-xl md:text-3xl xl:text-5xl pl-3 mb-1 text-white">{{ welcomeText }}<span class="animate-pulse">|</span></p>

        <!-- CV Buttons -->
        <!-- <div class="flex md:pt-5 2xl:pt-24">
          <button @click="openModal(cvFetchLink, 'Download')" class="hidden dark:block cv-button bg-gradient-to-r from-blue-400 to-blue-600 dark:from-red-400 dark:to-red-600 shadow-lg border-b-2 border-slate-50 text-white font-bold text-sm md:text-xl px-5 md:py-6 2xl:px-0 rounded-full w-38 md:w-44 mr-2 md:mr-44 2xl:mr-64">{{ cvFetchText }}</button>
          <button @click="openModal(cvWatchLink, 'Watch')" class="block dark:hidden cv-button bg-gradient-to-r from-blue-400 to-blue-600 dark:from-red-400 dark:to-red-600 shadow-lg border-b-2 border-slate-50 text-white font-bold text-sm md:text-xl px-5 md:py-6 2xl:px-0 rounded-full w-38 md:w-44 mr-2 md:mr-44 2xl:mr-64">{{ cvWatchText }}</button>
          <button @click="openModal(cvWatchLink, 'Watch')" class="hidden dark:block cv-button bg-gradient-to-r from-blue-400 to-blue-600 dark:from-blue-400 dark:to-blue-600 shadow-lg border-b-2 border-slate-50 text-white font-bold text-sm md:text-xl px-5 md:py-6 2xl:px-0 rounded-full w-38 md:w-44">{{ cvWatchText }}</button>
          <button @click="openModal(cvFetchLink, 'Download')" class="block dark:hidden cv-button bg-gradient-to-r from-red-400 to-red-600 dark:from-red-400 dark:to-red-600 shadow-lg border-b-2 border-slate-50 text-white font-bold text-sm md:text-xl px-5 md:py-6 2xl:px-0 rounded-full w-38 md:w-44">{{ cvFetchText }}</button>
        </div> -->

        <div class="flex md:pt-5 2xl:pt-24">
  <button @click="openModal(cvFetchLink, 'Download')" class="hidden dark:block button bg-red-500  shadow-lg border-b-2 border-slate-50 text-white font-bold text-sm md:text-xl px-5 md:py-6 2xl:px-0 rounded-full w-38 md:w-44 mr-2 md:mr-44 2xl:mr-64">
    <span>{{ cvFetchText }}</span>
    <div class="liquid"></div>
  </button>
  <button @click="openModal(cvWatchLink, 'Watch')" class="block dark:hidden button bg-blue-500 shadow-lg border-b-2 border-slate-50 text-white font-bold text-sm md:text-xl px-5 md:py-6 2xl:px-0 rounded-full w-38 md:w-44 mr-2 md:mr-44 2xl:mr-64">
    <span>{{ cvWatchText }}</span>
    <div class="liquid2"></div>
  </button>
  <button @click="openModal(cvWatchLink, 'Watch')" class="hidden dark:block button bg-blue-500 shadow-lg border-b-2 border-slate-50 text-white font-bold text-sm md:text-xl px-5 md:py-6 2xl:px-0 rounded-full w-38 md:w-44">
    <span>{{ cvWatchText }}</span>
    <div class="liquid2"></div>
  </button>
  <button @click="openModal(cvFetchLink, 'Download')" class="block dark:hidden button bg-red-500 shadow-lg border-b-2 border-slate-50 text-white font-bold text-sm md:text-xl px-5 md:py-6 2xl:px-0 rounded-full w-38 md:w-44">
    <span>{{ cvFetchText }}</span>
    <div class="liquid"></div>
  </button>
</div>



      </div>
    </div>

    <!-- Modal -->
    <div v-if="showModal" class="fixed inset-0 z-50 overflow-auto bg-black bg-opacity-75 flex justify-center items-center">
      <div class="bg-white rounded-lg p-8">
        
        <!-- Video CV -->
        <div v-if="isVideoCvVisible" class="mb-4">
          <h3 class="text-lg font-bold mb-2">Video CV</h3>
          <video controls autoplay class=" w-64 xl:w-[1000px] xl:h-[500px] " :src="cvWatchLink" alt="Video CV"></video>
        </div>
        <!-- PDF Viewer -->
        <div v-if="isPdfCvVisible" class="mb-4">
          
          
        </div>
        <!-- Download CV -->
        <div v-if="isDownloadCvVisible">
         
          <iframe :src="cvFetchLink" class="w-64 h-32 xl:w-[1000px] xl:h-[500px]" frameborder="0"></iframe>
          <a :href="cvFetchLink" class="text-blue-500">{{ cvFetchText }}</a>
        </div>
        <button @click="closeModal" class="mt-4 px-4 py-2 text-sm w-full bg-blue-500 rounded-full text-white hover:bg-blue-600">Close</button>
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

// Modal Control
const showModal = ref(false);
const isVideoCvVisible = ref(false);
const isPdfCvVisible = ref(false);
const isDownloadCvVisible = ref(false);

// Video CV source and CV download link



const openModal = (link, action) => {
  showModal.value = true;
  if (action === 'Watch') {
    isVideoCvVisible.value = true;
    isPdfCvVisible.value = false;
    isDownloadCvVisible.value = false;
  } else if (action === 'Preview') {
    isVideoCvVisible.value = false;
    isPdfCvVisible.value = true;
    isDownloadCvVisible.value = false;
  } else {
    isVideoCvVisible.value = false;
    isPdfCvVisible.value = false;
    isDownloadCvVisible.value = true;
  }
};

const closeModal = () => {
  showModal.value = false;
  isVideoCvVisible.value = false;
  isPdfCvVisible.value = false;
  isDownloadCvVisible.value = false;
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
  animation: pulse 0.3s cubic-bezier(0.4, 0, 0.6, 1) infinite;
}

</style>

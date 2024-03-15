<template>
  <div class="fixed inset-0 overflow-y-auto z-10">
    <div class="flex items-center justify-center min-h-screen pt-4 px-4 pb-20 text-center">
      <div class="fixed inset-0 transition-opacity" aria-hidden="true">
        <div class="absolute inset-0 bg-gray-500 opacity-75"></div>
      </div>
      <span class="hidden sm:inline-block sm:align-middle sm:h-screen" aria-hidden="true">&#8203;</span>
      <div class="inline-block bg-white rounded-lg text-left overflow-hidden shadow-xl transform transition-all my-8 align-middle w-[1200px]" >
        <div class="bg-white px-4 pt-5 pb-4">
          <!--  -->
          <iframe :src="websiteUrl" frameborder="0" allowfullscreen class="w-full h-[70vh]"></iframe>
        </div>
        <div class="bg-gray-50 px-4 py-3 flex flex-row-reverse">
          <button @click="$emit('closeModal')" type="button" class="inline-flex justify-center w-full rounded-full  px-4 py-2 bg-gradient-to-r from-blue-400 to-blue-600 dark:from-red-400 dark:to-red-600 font-medium text-white shadow-sm hover:bg-red-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-red-500 ml-3 text-sm">
            Close
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
const props = defineProps({
  websiteUrl: String
});
</script>

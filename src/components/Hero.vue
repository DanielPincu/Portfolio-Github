<template>
  <div class="lg:grid grid-cols-2 items-center pb-0 md:pb-20 xl:border-black xl:border-2 xl:rounded-full mt-20">
    <!-- intro start -->
    <div class="flex flex-col">
      <h1 class="text-3xl font-bold font-serif text-center ml-0 xl:ml-20">
        I’m Daniel Pincu <br> <span class="text-yellow-500">Front-end</span> Developer
      </h1>
      <p class="text-xl mx-10 mt-5 font-semibold">Designing and coding beautifully simple things requires a blend of creativity, technical skill, and attention to detail. It's a craft that involves finding elegant solutions to complex problems, all while keeping the end user in mind.</p>
      <a v-for="(button, index) in buttons" :key="index" :href="button.target" @click.prevent="scrollToElement(button.target)">
        <div class="text-xl bg-red-700 mt-10 p-5 md:ml-10 ml-0 w-30 rounded-full text-center hover:bg-yellow-700 hover:text-white transition-all duration-400 dark:bg-blue-700">{{ button.text }}</div>
      </a>
    </div>
    <!-- intro ends -->

    <!-- image start -->
    <div class="flex justify-center">
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
</script>

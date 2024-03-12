<template>
  <div class="shadow-xl rounded-3xl mt-20 px-20 pb-20 bg-blue-200 dark:bg-red-200" :id="aboutId">
    <div>
      <div class="flex justify-center">
        <h1 class="text-4xl pt-10 pb-10">About Me</h1>
      </div>
      <div class="grid lg:grid-cols-2">
        <div>
          <p v-for="(paragraph, index) in paragraphs" :key="index" class="mb-5 text-xl">{{ paragraph }}</p>
        </div>
        <div class="hidden lg:block">
          <img class="w-96 ml-20" :src="imageSrc" alt="">
        </div>
      </div>

      <button class="py-5" @click="toggleReadMore">{{ buttonText }}</button>

      <div v-show="isReadMore">
        <p v-for="(paragraph, index) in extraParagraphs" :key="index">{{ paragraph }}</p>

        <button @click="toggleReadMore">{{ buttonText }}</button>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue';

const isReadMore = ref(false);

const toggleReadMore = () => {
  isReadMore.value = !isReadMore.value;
};

const buttonText = computed(() => {
  return isReadMore.value ? 'Read less' : 'Read more...';
});

const paragraphs = ref([
  "Hey, my name is Daniel Pincu, and I've got a knack for turning ideas into reality. As a multimedia designer, I thrive on simplicity with a splash of creativity.",
  "Whether it's crafting sleek logos or dreaming up responsive websites, I'm always up for a challenge. Variety is the spice of life, and I love diving into different projects to discover new ways to make them shine.",
]);

const extraParagraphs = ref([
  "My mission? Making things look awesome! From logos that leave a lasting impression to motion graphics that bring static images to life, I've got a bit of everything up my sleeve. User interfaces? Consider it done. I'm here to sprinkle a little magic on your project and make it stand out from the crowd."
]);

const imageSrc = ref("src/assets/img/MiniMe.jpg");
</script>



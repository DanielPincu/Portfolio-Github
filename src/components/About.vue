<template>
  <div class="border-b-2 border-zinc-200 pb-20">
    <div class="shadow-xl rounded-3xl mt-20 px-5 2xl:px-14 pb-20 bg-blue-200 dark:bg-red-200">
    <div>
      <div class="flex justify-center">
        <h1 class="text-4xl py-10">About Me</h1>
      </div>
      <div class="grid xl:grid-cols-2 gap-10 grid-cols-1">
        <div>
          <p v-for="(paragraph, index) in paragraphs" :key="index" class="mb-5 text-xl max-2xl:pl-5">{{ paragraph }}</p>
        </div>
        <div class="hidden lg:block">
          <img class="rounded-3xl" :src="imageSrc" alt="">
        </div>
      </div>

      <button v-if="!isReadMore" class="py-5 px-5" @click="toggleReadMore">{{ buttonText }}</button>

      <div v-show="isReadMore">
        <p class="py-10 pl-5 italic md:mx-20" v-for="(paragraph, index) in extraParagraphs" :key="index">{{ paragraph }}</p>

        <button class="px-5" @click="toggleReadMore">{{ buttonText }}</button>
      </div>
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
  "My mission? Making things look awesome! From logos that leave a lasting impression to motion graphics that bring static images to life, I've got a bit of everything up my sleeve. User interfaces? Consider it done. I'm here to sprinkle a little magic on your project and make it stand out from the crowd.",
]);

const extraParagraphs = ref([
  "Did I catched your attention? I'm always on the lookout for new opportunities. If you've got a project that needs a little extra flair, feel free to drop me a message. Let us make things come true!",
  '"The choice has always been yours..." - Morpheus',
]);

const imageSrc = ref("/assets/img/daniel.png");


</script>

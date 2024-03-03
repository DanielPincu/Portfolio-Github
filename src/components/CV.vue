<template>
  <div id="home">
    <!-- Profile Info -->
    <div>
      <div class="flex justify-center">
        <img class="w-48 mt-10" :src="profile.image" :alt="profile.name">
      </div>
      <div class="border-b-2 border-zinc-400 pb-5">
        <h1 class="text-2xl font-bold text-center mt-5">{{ profile.name }}</h1>
        <p class="text-center text-gray-500">{{ profile.title }}</p>
      </div>
      <!-- Additional sections -->
      <div v-for="(additionalSection, index) in additionalSections" :key="'additionalSection' + index" class="mx-10 mt-5 flex flex-col bg-slate-200 rounded-full items-center justify-end h-16">
        <h1 class="text-xl bg-gray-300 rounded-full px-4">{{ additionalSection.title }}</h1>
        <p class="text-xl">{{ additionalSection.content }}</p>
      </div>
     
    </div>

    <!-- Dynamic Sections -->
    <div v-for="(section, index) in dynamicSections" :key="index" class="pb-5">
      <h1 class="font-bold text-2xl text-center pt-5">{{ section.title }}</h1>
      <div v-for="(item, idx) in section.items" :key="idx" class="mx-10 my-5 flex flex-col bg-slate-200 rounded-full items-center h-16 justify-center">
        <h1 class="text-xl font-bold px-4">{{ item.name }}</h1>
        <div class="w-32 2xl:w-64 bg-gray-500 rounded-full dark:bg-gray-700">
          <div class="bg-blue-500 dark:bg-red-500 text-xs font-bold text-center text-white p-1 leading-none rounded-full" :style="{ width: item.percentage }">{{ item.percentage }}</div>
        </div>
      </div>
    </div>
  </div>


  <div class="mt-5 pt-10 text-center bg-white shadow-2xl rounded-3xl ml-5 h-[390px] sticky top-10">
        <h1 class="text-2xl font-bold">Contact information</h1>
        <p>
          <strong>Email:</strong> email@example.com <br>
          <strong>Phone number:</strong> 123-456-7890 <br>
          <strong>Address:</strong> 1234 Street Name, City, Country
        </p>
        <!-- Add your contact information here -->
    </div>


</template>

<script setup>
import { onMounted } from 'vue';
import anime from 'animejs';

const profile = {
  name: "Daniel Pincu",
  title: "Front-end Developer",
  image: "src/assets/img/pd.png"
};

const dynamicSections = [
  {
    title: "Languages",
    items: [
      { name: "Romanian", percentage: "100%" },
      { name: "English", percentage: "80%" },
      { name: "Danish", percentage: "20%" }
      // Add more languages as needed
    ]
  },
  {
    title: "Skills",
    items: [
      { name: "HTML/CSS", percentage: "80%" },
      { name: "Bootstrap", percentage: "80%" },
      { name: "TailwindCSS", percentage: "80%" },
      { name: "Wordpress", percentage: "50%" },
      { name: "VueJS", percentage: "40%" },
      { name: "ReactJS", percentage: "20%"}
      // Add more skills as needed
    ]
  },
  // Your existing dynamic sections data here
];

// Additional sections data
const additionalSections = [
  {
    title: "Age:",
    content: "32"
  },
  {
    title: "Residence:",
    content: "Denmark"
  },
  {
    title: "Location:",
    content: "Esbjerg"
  },
  {
    title: "Freelance:",
    content: "Available"
  }
];

onMounted(() => {
  anime({
    targets: '.tt',
    opacity: [0, 1],
    translateY: [-500, 0],
    translateX: [400, 0], 
    easing: "linear",
    duration: 3000,
  });
});
</script>

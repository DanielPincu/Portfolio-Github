<script setup>

import CV from './components/CV.vue'
import Hero from './components/Hero.vue'
import Services from './components/Services.vue'
import Nav from './components/Nav.vue'
import Portfolio from './components/Portfolio.vue'
import About from './components/About.vue'
import Contact from './components/Contact.vue'
import Footer from './components/Footer.vue'

import { ref } from 'vue';

const homeId = ref('home');
const portfolioId = ref('portfolio');
const contactId = ref('contact');
const aboutId = ref('about');

</script>



<template>
   

<main class="lg:grid grid-cols-12">


<!-- Left Column -->
    <div class="col-span-3 hidden lg:block pb-5">
        
        <CV />

    </div>


<!-- Center Column -->
    <div class="lg:col-span-8 col-span-12 mx-5">

        <Hero :id="homeId" />
        <Services />
        <Portfolio :id="portfolioId" />
        <About :id="aboutId"/>
        <Contact :id="contactId" />

    </div>














<!-- Right Column -->
    <div class="col-span-1 hidden lg:block mr-5 rounded-full xl:bg-blue-100 xl:dark:bg-red-100">

        <Nav />

    </div>



</main>
    
  
<Footer />


</template>


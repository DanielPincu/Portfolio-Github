<script setup>
  import CV from './components/CV.vue'
  import Hero from './components/Hero.vue'
  import Services from './components/Services.vue'
  import Nav from './components/Nav.vue'
  import Portfolio from './components/Portfolio.vue'
  import About from './components/About.vue'
  import Contact from './components/Contact.vue'
  import Footer from './components/Footer.vue'

  // Function to check if the device is a mobile device
  const isMobileDevice = () => {
    return window.innerWidth <= 768; // Adjust the breakpoint as needed
  };

  // It stops the stupid animation on mobile devices
  if (!isMobileDevice()) {
    import('aos').then(module => {
      const AOS = module.default;
      import('aos/dist/aos.css').then(() => {
        AOS.init({
          once: true,
        });
      });
    });
  }
</script>



<template>
   

<main class="lg:grid grid-cols-12">


<!-- Left Column -->
    <div class="col-span-3 hidden lg:block pb-5 border-r-2 border-zinc-200">
        
        <CV />

    </div>


<!-- Center Column -->
    <div class="lg:col-span-8 col-span-12 mx-5">

        <Hero />
        <Services />
        <Portfolio />
        <About />
        <Contact />

    </div>
    

<!-- Right Column -->
    <div class="col-span-1 hidden lg:block rounded-full xl:bg-blue-100 xl:dark:bg-red-100 xl:border-2 xl:border-blue-300 xl:dark:border-red-300" 
    
    data-aos="fade-left"
    data-aos-duration="2000"
    
    >

        <Nav />

    </div>



</main>
    
  
<Footer />


</template>


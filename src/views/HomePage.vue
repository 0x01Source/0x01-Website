<template>
    <div class="sections">
        <div class="section">
   <nav-bar></nav-bar>
   <header-home></header-home>
</div>
<div class="section">
   <section-home></section-home>
</div>
<div class="section">
   <projects-home></projects-home>
</div>
<div class="section">
   <pricing-home></pricing-home>
</div>
<div class="section">
   <contact-us></contact-us>
</div>
<div class="section">
   <footer-home></footer-home>
</div>
  </div>
  </template>
  
  <script>
    import NavBar from '@/components/NavBar.vue';
    import HeaderHome from '@/components/HeaderHome.vue';
    import SectionHome from '@/components/SectionHome.vue';
    import ProjectsHome from '@/components/ProjectsHome.vue';
    import PricingHome from '@/components/PricingHome.vue';
    import ContactUs from '@/components/ContactUs.vue';
    import FooterHome from '@/components/FooterHome.vue';
  export default {
    components:{
      NavBar,
      HeaderHome,
      SectionHome,
      ProjectsHome,
      PricingHome,
      ContactUs,
      FooterHome,
    }
  }
  </script>
  
  <style>

  
  </style>
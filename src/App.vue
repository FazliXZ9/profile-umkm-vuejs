<script setup>
import Navbar from './components/Navbar.vue'
import HeroSection from './components/HeroSection.vue'
import AboutSection from './components/AboutSection.vue'
import ServicesSection from './components/ServicesSection.vue'
import FeaturesSection from './components/FeaturesSection.vue'
import FooterSection from './components/FooterSection.vue'
import ServiceCatalog from './components/ServiceCatalog.vue'
</script>

<!-- <template>
  <div class="min-h-screen font-sans text-gray-800">
    <Navbar />
    <main>
      <HeroSection />
      <AboutSection />
      <ServicesSection />
      <FeaturesSection />
    </main>
    <FooterSection />
  </div>
</template> -->

<template>
  <div class="min-h-screen font-sans text-gray-800">
    <Navbar />
    <main>
      <HeroSection />
      <AboutSection />
      
      <ServiceCatalog /> <FeaturesSection />
    </main>
    <FooterSection />
  </div>
</template>

<style>
/* Pastikan main.css sudah diimport di main.js Anda */
</style>
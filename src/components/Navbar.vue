<script setup>
const navItems = ['Beranda', 'Tentang Kami', 'Layanan', 'Keunggulan', 'Kontak']
const activeItem = 'Beranda' // Simulasi item yang aktif
</script>

<template>
  <nav class="bg-enp-dark text-white py-4 px-6 md:px-12 flex items-center justify-between fixed w-full top-0 z-50 shadow-lg">
    <div class="flex items-center space-x-3">
      <img 
        src="@/assets/logo-atas.png" 
        alt="Logo ENP Group" 
        class="h-10 w-auto object-contain" 
      />
      
      <span class="text-xl font-bold tracking-wider">ENP GROUP</span>
    </div>

    <ul class="hidden md:flex space-x-8 font-medium">
      <li v-for="item in navItems" :key="item" class="relative group cursor-pointer">
        <a href="#" :class="item === activeItem ? 'text-enp-gold' : 'hover:text-enp-gold transition'">
          {{ item }}
        </a>
        <div v-if="item === activeItem" class="absolute -bottom-1 left-0 w-8 h-1 bg-enp-gold rounded-full"></div>
      </li>
    </ul>

    <div class="hidden md:block">
      <button class="bg-enp-gold hover:bg-enp-gold-hover text-enp-dark font-bold py-2 px-6 rounded transition">
        HUBUNGI KAMI
      </button>
    </div>
    
    <div class="md:hidden text-enp-gold">
        <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-8 h-8">
          <path stroke-linecap="round" stroke-linejoin="round" d="M3.75 6.75h16.5M3.75 12h16.5m-16.5 5.25h16.5" />
        </svg>
    </div>
  </nav>
</template>
<script setup>
import { ref } from 'vue'

const navItems = ['Beranda', 'Tentang Kami', 'Layanan', 'Keunggulan']
const activeItem = 'Beranda'

const isMenuOpen = ref(false)

const toggleMenu = () => {
  isMenuOpen.value = !isMenuOpen.value
}
</script>

<template>
  <nav class="bg-enp-dark text-white py-4 px-6 md:px-12 fixed w-full top-0 z-50 shadow-lg transition-all duration-300">
    <div class="flex items-center justify-between">
      
      <div class="flex items-center space-x-3 cursor-pointer hover:opacity-80 transition">
        <img 
          src="@/assets/logo-Update2.png" 
          alt="Logo ENP Group" 
          class="h-10 w-auto object-contain" 
        />
      </div>

      <ul class="hidden md:flex space-x-8 font-medium">
        <li v-for="item in navItems" :key="item" class="relative group cursor-pointer">
          <a href="#" :class="item === activeItem ? 'text-enp-gold' : 'hover:text-enp-gold transition duration-300'">
            {{ item }}
          </a>
          <span 
            class="absolute -bottom-1 left-0 h-1 bg-enp-gold rounded-full transition-all duration-300 ease-in-out"
            :class="item === activeItem ? 'w-8' : 'w-0 group-hover:w-full'"
          ></span>
        </li>
      </ul>

      <div class="hidden md:block">
        <button class="bg-enp-gold hover:bg-enp-gold-hover text-enp-dark font-bold py-2 px-6 rounded transition transform hover:scale-105 duration-200">
          HUBUNGI KAMI
        </button>
      </div>
      
      <button 
        @click="toggleMenu" 
        class="md:hidden text-enp-gold focus:outline-none p-2 transition-transform duration-300"
        :class="isMenuOpen ? 'rotate-90' : 'rotate-0'"
      >
          <svg v-if="!isMenuOpen" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-8 h-8">
            <path stroke-linecap="round" stroke-linejoin="round" d="M3.75 6.75h16.5M3.75 12h16.5m-16.5 5.25h16.5" />
          </svg>

          <svg v-else xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-8 h-8">
            <path stroke-linecap="round" stroke-linejoin="round" d="M6 18L18 6M6 6l12 12" />
          </svg>
      </button>
    </div>

    <transition
      enter-active-class="transition duration-300 ease-out origin-top"
      enter-from-class="transform -translate-y-4 opacity-0 scale-y-95"
      enter-to-class="transform translate-y-0 opacity-100 scale-y-100"
      leave-active-class="transition duration-200 ease-in origin-top"
      leave-from-class="transform translate-y-0 opacity-100 scale-y-100"
      leave-to-class="transform -translate-y-4 opacity-0 scale-y-95"
    >
      <div v-if="isMenuOpen" class="md:hidden absolute top-full left-0 w-full bg-enp-dark border-t border-gray-700 shadow-xl flex flex-col overflow-hidden">
        <ul class="flex flex-col p-4 space-y-4 font-medium text-center">
          <li v-for="(item, index) in navItems" :key="item" class="animate-fadeIn" :style="{ animationDelay: `${index * 100}ms` }">
            <a 
              href="#" 
              class="block py-2 hover:text-enp-gold transition duration-200 hover:translate-x-1"
              :class="item === activeItem ? 'text-enp-gold font-bold' : ''"
              @click="isMenuOpen = false" 
            >
              {{ item }}
            </a>
          </li>
          <li class="pt-2 animate-fadeIn" style="animation-delay: 500ms">
             <button class="w-full bg-enp-gold hover:bg-enp-gold-hover text-enp-dark font-bold py-3 px-6 rounded transition active:scale-95">
              HUBUNGI KAMI
            </button>
          </li>
        </ul>
      </div>
    </transition>
  </nav>
</template>

<style scoped>
/* Keyframes sederhana untuk item menu mobile muncul satu per satu */
@keyframes fadeIn {
  from { opacity: 0; transform: translateY(-10px); }
  to { opacity: 1; transform: translateY(0); }
}

.animate-fadeIn {
  animation: fadeIn 0.4s ease-out forwards;
  opacity: 0; /* Mulai hidden sebelum animasi jalan */
}
</style>
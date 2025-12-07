<script setup>
const services = [
  {
    title: 'Tech',
    description: 'Solusi teknologi digital, pengembangan web, dan integrasi sistem untuk modernisasi bisnis Anda.',
    iconPath: 'M9 17.25v1.007a3 3 0 01-.879 2.122L7.5 21h9l-.621-.621A3 3 0 0115 18.257V17.25m6-12V15a2.25 2.25 0 01-2.25 2.25H5.25A2.25 2.25 0 013 15V5.25m18 0A2.25 2.25 0 0018.75 3H5.25A2.25 2.25 0 003 5.25m18 0V12a2.25 2.25 0 01-2.25 2.25H5.25A2.25 2.25 0 013 12V5.25' // Icon Komputer
  },
  {
    title: 'Textile',
    description: 'Layanan produksi tekstil dan garmen berkualitas tinggi dengan inovasi bahan dan desain terkini.',
    iconPath: 'M15.75 9V5.25A2.25 2.25 0 0013.5 3h-3a2.25 2.25 0 00-2.25 2.25V9m7.5 0H7.5m0 0v4.5a3 3 0 11-6 0V9m18 0v4.5a3 3 0 11-6 0V9m-9 4.5v6.75a2.25 2.25 0 002.25 2.25h3a2.25 2.25 0 002.25-2.25V13.5' // Icon Baju (Mendekati)
  },
  {
    title: 'Culinary',
    description: 'Dukungan pengembangan produk kuliner, standarisasi resep, dan strategi pemasaran F&B.',
    iconPath: 'M12 6v12m-3-2.818l.879.659c1.171.879 3.07.879 4.242 0 1.172-.879 1.172-2.303 0-3.182C13.536 12.219 12.768 12 12 12c-.725 0-1.45-.22-2.003-.659-1.106-.879-1.106-2.303 0-3.182s2.9-.879 4.006 0l.415.33M21 12a9 9 0 11-18 0 9 9 0 0118 0z' // Icon Makanan (Mendekati - piring/saji)
  },
]
</script>

<template>
  <section class="py-20 px-6 md:px-12 bg-gray-50">
    <div class="max-w-7xl mx-auto text-center">
      <h2 class="text-3xl md:text-4xl font-bold text-enp-dark mb-16 relative inline-block">
        Our Services
        <div class="absolute left-1/2 transform -translate-x-1/2 -bottom-4 w-16 h-1 bg-enp-gold rounded-full"></div>
      </h2>

      <div class="grid md:grid-cols-3 gap-12">
        <div v-for="(service, index) in services" :key="index" class="flex flex-col items-center p-6 transition hover:-translate-y-2">
          <div class="w-20 h-20 mb-6 text-enp-gold p-4 border-2 border-enp-gold rounded-2xl flex items-center justify-center">
             <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-10 h-10">
              <path stroke-linecap="round" stroke-linejoin="round" :d="service.iconPath" />
            </svg>
          </div>
          <h3 class="text-xl font-bold text-enp-dark mb-3">{{ service.title }}</h3>
          <p class="text-gray-600 max-w-xs mx-auto">{{ service.description }}</p>
        </div>
      </div>
    </div>
  </section>
</template>
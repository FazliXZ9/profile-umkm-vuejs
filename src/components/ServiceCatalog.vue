<script setup>
import { ref, computed, onMounted } from 'vue'
import axios from 'axios'

const services = ref([])
const imageBaseUrl = ref('')
const isLoading = ref(true)
const activeCategory = ref('Semua')

const fetchData = async () => {
  try {
    const response = await axios.get('https://enpadmin.sainzlab.my.id/api/landing-data')
    
    if (response.data.status === 'success') {
      services.value = response.data.data.services
      imageBaseUrl.value = response.data.data.image_base_url
    }
  } catch (error) {
    console.error("Gagal mengambil data layanan:", error)
  } finally {
    isLoading.value = false
  }
}

onMounted(() => {
  fetchData()
})

const categories = computed(() => {
  const uniqueCats = new Set(services.value.map(item => item.category))
  return ['Semua', ...uniqueCats]
})

const filteredServices = computed(() => {
  if (activeCategory.value === 'Semua') {
    return services.value
  }
  return services.value.filter(item => item.category === activeCategory.value)
})

const getImageUrl = (path) => {
  if (!path) return 'https://placehold.co/600x400/e2e8f0/1e293b?text=No+Image'
  return `${imageBaseUrl.value}/${path}`
}

const getPrice = (item) => {
  return item.price ? item.price : 'Hubungi Admin'
}

const contactWhatsapp = (productName) => {
  const message = `Halo Admin ENP Group, saya tertarik dengan layanan ${productName}, bisa minta info detail?`
  const url = `https://wa.me/6282320305330?text=${encodeURIComponent(message)}`
  window.open(url, '_blank')
}
</script>

<template>
  <section class="py-20 px-6 md:px-12 bg-gray-50" id="layanan-lengkap">
    <div class="max-w-7xl mx-auto">
      
      <div class="text-center mb-12">
        <h2 class="text-3xl md:text-4xl font-bold text-enp-dark mb-4">Katalog Layanan</h2>
        <p class="text-gray-600 max-w-2xl mx-auto">
          Temukan solusi terpadu untuk kebutuhan harian Anda. Kami menawarkan beragam layanan mulai dari perawatan kendaraan, kebutuhan digital, kreasi fesyen, hingga camilan lezat.
        </p>
      </div>

      <div v-if="isLoading" class="flex justify-center items-center py-20">
        <div class="animate-spin rounded-full h-12 w-12 border-b-2 border-enp-gold"></div>
        <span class="ml-3 text-gray-500 font-medium">Memuat Layanan...</span>
      </div>

      <div v-else>
        <div class="flex flex-wrap justify-center gap-4 mb-12">
          <button 
            v-for="cat in categories" 
            :key="cat"
            @click="activeCategory = cat"
            :class="[
              'px-6 py-2 rounded-full font-semibold transition-all duration-300 border-2',
              activeCategory === cat 
                ? 'bg-enp-dark text-white border-enp-dark' 
                : 'bg-white text-gray-500 border-gray-200 hover:border-enp-gold hover:text-enp-gold'
            ]"
          >
            {{ cat }}
          </button>
        </div>

        <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-8">
          <div 
            v-for="item in filteredServices" 
            :key="item.id" 
            class="bg-white rounded-2xl overflow-hidden shadow-lg hover:shadow-2xl transition-all duration-300 transform hover:-translate-y-2 group"
          >
            <div class="relative h-56 overflow-hidden bg-gray-200">
              <img 
                :src="getImageUrl(item.image_path)" 
                :alt="item.title" 
                class="w-full h-full object-cover transition-transform duration-500 group-hover:scale-110"
                @error="$event.target.src = 'https://placehold.co/600x400/e2e8f0/1e293b?text=Error+Loading'"
              />
              <div class="absolute top-4 right-4 bg-enp-gold text-enp-dark text-xs font-bold px-3 py-1 rounded-full uppercase tracking-wider">
                {{ item.category }}
              </div>
            </div>

            <div class="p-6">
              <h3 class="text-xl font-bold text-enp-dark mb-2">{{ item.title }}</h3>
              <p class="text-gray-600 text-sm mb-4 line-clamp-2">
                {{ item.description }}
              </p>
              
              <div class="flex items-center justify-between mt-4 pt-4 border-t border-gray-100">
                <span class="text-enp-dark font-semibold text-sm">{{ getPrice(item) }}</span>
                
                <button 
                  @click="contactWhatsapp(item.title)"
                  class="flex items-center gap-2 text-enp-gold hover:text-enp-gold-hover font-bold text-sm transition"
                >
                  Konsultasi
                  <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" class="w-4 h-4">
                    <path stroke-linecap="round" stroke-linejoin="round" d="M13.5 4.5L21 12m0 0l-7.5 7.5M21 12H3" />
                  </svg>
                </button>
              </div>
            </div>
          </div>
        </div>

        <div v-if="filteredServices.length === 0" class="text-center py-20 bg-white rounded-xl shadow-sm border border-gray-100">
          <p class="text-gray-500 text-lg">Belum ada layanan di kategori ini.</p>
        </div>
      </div>

    </div>
  </section>
</template>
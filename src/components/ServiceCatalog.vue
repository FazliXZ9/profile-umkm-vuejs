<script setup>
import { ref, computed } from 'vue'

// 1. Data Mockup Layanan (Bisa ditambah sesuai kebutuhan)
const services = [
  {
    id: 1,
    category: 'Tech',
    title: 'Web Company Profile',
    description: 'Pembuatan website profesional untuk meningkatkan kredibilitas bisnis Anda. Responsive dan SEO friendly.',
    price: 'Mulai Rp 1.5jt',
    image: 'https://placehold.co/600x400/0a192f/fbbf24?text=Web+Dev'
  },
  {
    id: 2,
    category: 'Textile',
    title: 'Seragam Kerja Custom',
    description: 'Produksi seragam kantor, pabrik, atau komunitas dengan bahan drill/katun berkualitas tinggi.',
    price: 'Min. 12 Pcs',
    image: 'https://placehold.co/600x400/fbbf24/0a192f?text=Seragam+Kerja'
  },
  {
    id: 3,
    category: 'Culinary',
    title: 'Paket Usaha Franchise',
    description: 'Paket lengkap usaha kuliner (gerobak, bahan baku, peralatan) siap jualan.',
    price: 'Hubungi Admin',
    image: 'https://placehold.co/600x400/1e293b/ffffff?text=Franchise'
  },
  {
    id: 4,
    category: 'Tech',
    title: 'Aplikasi Kasir (POS)',
    description: 'Sistem kasir terintegrasi untuk memantau stok dan penjualan secara real-time.',
    price: 'Langganan Bulanan',
    image: 'https://placehold.co/600x400/0a192f/fbbf24?text=App+Kasir'
  },
  {
    id: 5,
    category: 'Textile',
    title: 'Kaos Sablon & Event',
    description: 'Sablon plastisol/DTF awet untuk kaos event, gathering, atau merchandise.',
    price: 'Harga Bersaing',
    image: 'https://placehold.co/600x400/fbbf24/0a192f?text=Kaos+Event'
  },
  {
    id: 6,
    category: 'Culinary',
    title: 'Supply Bahan Baku',
    description: 'Supplier biji kopi, bumbu premix, dan powder minuman untuk cafe/resto.',
    price: 'Grosir',
    image: 'https://placehold.co/600x400/1e293b/ffffff?text=Bahan+Baku'
  },
]

// 2. Logic Filter Kategori
const activeCategory = ref('Semua')
const categories = ['Semua', 'Tech', 'Textile', 'Culinary']

const filteredServices = computed(() => {
  if (activeCategory.value === 'Semua') {
    return services
  }
  return services.filter(item => item.category === activeCategory.value)
})

// 3. Fungsi ke WhatsApp
const contactWhatsapp = (productName) => {
  const message = `Halo Admin ENP Group, saya tertarik dengan layanan ${productName}, bisa minta info detail?`
  const url = `https://wa.me/6281234567890?text=${encodeURIComponent(message)}`
  window.open(url, '_blank')
}
</script>

<template>
  <section class="py-20 px-6 md:px-12 bg-gray-50" id="layanan-lengkap">
    <div class="max-w-7xl mx-auto">
      
      <div class="text-center mb-12">
        <h2 class="text-3xl md:text-4xl font-bold text-enp-dark mb-4">Katalog Layanan</h2>
        <p class="text-gray-600 max-w-2xl mx-auto">
          Temukan solusi terbaik yang sesuai dengan kebutuhan bisnis Anda. Kami menawarkan layanan terintegrasi dari hulu ke hilir.
        </p>
      </div>

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
          <div class="relative h-56 overflow-hidden">
            <img 
              :src="item.image" 
              :alt="item.title" 
              class="w-full h-full object-cover transition-transform duration-500 group-hover:scale-110"
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
              <span class="text-enp-dark font-semibold text-sm">{{ item.price }}</span>
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

      <div v-if="filteredServices.length === 0" class="text-center py-20">
        <p class="text-gray-500">Belum ada layanan di kategori ini.</p>
      </div>

    </div>
  </section>
</template>
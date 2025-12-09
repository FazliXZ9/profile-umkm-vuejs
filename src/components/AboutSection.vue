<script setup>
import { ref, onMounted } from 'vue'
import axios from 'axios'

// State untuk menampung data
const description = ref('')
const imageUrl = ref('')
const isLoading = ref(true)

// Data Default (Fallback jika database kosong)
const defaultDesc = `Kami hadir sebagai solusi terpadu untuk kebutuhan harian Anda. Dari perawatan kendaraan, kreasi fesyen personal, hingga konektivitas digital dan camilan lezat, kami berkomitmen menyediakan layanan UMKM yang beragam dan berkualitas.\n\nKami percaya bahwa bisnis lokal harus didukung dengan keahlian profesional dan layanan yang mudah diakses. Kami adalah mitra yang siap mendukung setiap aspek kebutuhan Anda.`
const defaultImage = 'https://placehold.co/600x400/e2e8f0/1e293b?text=Foto+UMKM'

const fetchData = async () => {
  try {
    const response = await axios.get('http://127.0.0.1:8000/api/landing-data')
    
    if (response.data.status === 'success') {
      const profile = response.data.data.profile
      const baseUrl = response.data.data.image_base_url

      // Jika ada data profil dari database, pakai data itu
      if (profile) {
        description.value = profile.about_description || defaultDesc
        
        if (profile.image_path) {
          imageUrl.value = `${baseUrl}/${profile.image_path}`
        } else {
          imageUrl.value = defaultImage
        }
      } else {
        // Jika tabel kosong, pakai default
        description.value = defaultDesc
        imageUrl.value = defaultImage
      }
    }
  } catch (error) {
    console.error("Gagal mengambil data profil:", error)
    // Jika error, tetap tampilkan default agar tidak rusak
    description.value = defaultDesc
    imageUrl.value = defaultImage
  } finally {
    isLoading.value = false
  }
}

onMounted(() => {
  fetchData()
})
</script>

<template>
  <section class="py-20 px-6 md:px-12 bg-white" id="tentang-kami">
    <div class="max-w-7xl mx-auto grid md:grid-cols-2 gap-12 items-center">
      
      <div class="rounded-2xl overflow-hidden shadow-xl h-[400px] bg-gray-100 relative">
        <div v-if="isLoading" class="absolute inset-0 flex items-center justify-center bg-gray-200 animate-pulse">
           <span class="text-gray-400">Loading Foto...</span>
        </div>

        <img 
          v-else
          :src="imageUrl" 
          alt="Tentang Kami" 
          class="w-full h-full object-cover hover:scale-105 transition duration-500"
          @error="$event.target.src = defaultImage" 
        >
      </div>

      <div class="space-y-6">
        <h2 class="text-3xl md:text-4xl font-bold text-enp-dark">Tentang Kami</h2>
        
        <div v-if="isLoading" class="space-y-3 animate-pulse">
          <div class="h-4 bg-gray-200 rounded w-full"></div>
          <div class="h-4 bg-gray-200 rounded w-5/6"></div>
          <div class="h-4 bg-gray-200 rounded w-full"></div>
        </div>

        <p v-else class="text-gray-600 leading-relaxed whitespace-pre-line">
          {{ description }}
        </p>
      </div>

    </div>
  </section>
</template>
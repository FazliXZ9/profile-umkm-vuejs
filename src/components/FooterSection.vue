<script setup>
const currentYear = new Date().getFullYear()
</script>

<template>
  <footer class="bg-enp-dark text-white pt-16 pb-8 px-6 md:px-12">
    <div class="max-w-7xl mx-auto grid md:grid-cols-3 gap-12 mb-12">
      
      <div class="flex flex-col items-start">
        <div class="flex items-center space-x-3 mb-6">
          <img 
            src="@/assets/logo-atas.png" 
            alt="Logo ENP Group" 
            class="h-12 w-auto object-contain" 
          />
          <span class="text-2xl font-bold tracking-wider">ENP GROUP</span>
        </div>

        <div class="flex items-start text-gray-300">
            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-5 h-5 mr-2 text-enp-gold mt-1 flex-shrink-0">
              <!-- <path stroke-linecap="round" stroke-linejoin="round" d="M15 10.5a3 3 0 11-6 0 3 3 0 016 0z" />
              <path stroke-linecap="round" stroke-linejoin="round" d="M19.5 10.5c0 7.142-7.5 11.25-7.5 11.25S4.5 17.642 4.5 10.5a7.5 7.5 0 1115 0z" /> -->
            </svg>
            <span class="leading-relaxed text-sm">
              Kp. Pasir Jati RT 002 / RW 001 Desa Cikaum Timur, <br>
              Kecamatan Cikaum Kabupaten Subang, Jawa Barat 41266
            </span>
        </div>
      </div>

      <div>
        <h3 class="text-lg font-bold mb-6">Contact Info</h3>
        <ul class="space-y-4 text-gray-300">
          
          <li class="flex items-center">
            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-5 h-5 mr-3 text-enp-gold flex-shrink-0"><path stroke-linecap="round" stroke-linejoin="round" d="M2.25 6.75c0 8.284 6.716 15 15 15h2.25a2.25 2.25 0 002.25-2.25v-1.372c0-.516-.351-.966-.852-1.091l-4.423-1.106c-.44-.11-.902.055-1.173.417l-1.36 1.744a15.09 15.09 0 01-7.07-7.07l1.744-1.36c.361-.271.526-.734.417-1.173L6.963 3.102a1.125 1.125 0 00-1.091-.852H4.5A2.25 2.25 0 002.25 4.5v2.25z" /></svg>
            0812-3456-7890
          </li>
          
          <li class="flex items-center">
             <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-5 h-5 mr-3 text-enp-gold flex-shrink-0"><path stroke-linecap="round" stroke-linejoin="round" d="M21.75 6.75v10.5a2.25 2.25 0 01-2.25 2.25h-15a2.25 2.25 0 01-2.25-2.25V6.75m19.5 0A2.25 2.25 0 0019.5 4.5h-15a2.25 2.25 0 00-2.25 2.25m19.5 0v.243a2.25 2.25 0 01-1.07 1.916l-7.5 4.615a2.25 2.25 0 01-2.36 0L3.32 8.91a2.25 2.25 0 01-1.07-1.916V6.75" /></svg>
            enpgroup25@gmail.com
          </li>

          <li class="flex items-center">
             <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-5 h-5 mr-3 text-enp-gold flex-shrink-0"><path stroke-linecap="round" stroke-linejoin="round" d="M12 21a9.004 9.004 0 008.716-6.747M12 21a9.004 9.004 0 01-8.716-6.747M12 21c2.485 0 4.5-4.03 4.5-9S12 3 12 3m0 18c-2.485 0-4.5-4.03-4.5-9S12 3 12 3m0 0a8.997 8.997 0 017.843 4.582M12 3a8.997 8.997 0 00-7.843 4.582m15.686 0A11.953 11.953 0 0112 10.5c-2.998 0-5.74-1.1-7.843-2.918m15.686 0A8.959 8.959 0 0121 12c0 .778-.099 1.533-.284 2.253m-17.132 0c.185-.72.284-1.475.284-2.253 0-1.46-.318-2.825-.885-4.04M12 5.25h.008v.008H12V5.25zm.375 0a.375.375 0 11-.75 0 .375.375 0 01.75 0zm0 5.25h.008v.008H12.375V10.5zm.375 0a.375.375 0 11-.75 0 .375.375 0 01.75 0zm0 5.25h.008v.008H12.375V15.75zm.375 0a.375.375 0 11-.75 0 .375.375 0 01.75 0z" /></svg>
            enpgroup.sainzlab.my.id
          </li>
        </ul>
      </div>
      
      <div>
        <h3 class="text-lg font-bold mb-6">Social Media</h3>
        <div class="flex space-x-4">
          <a href="https://www.tiktok.com/@enp.group?_r=1&_t=ZS-921bzNkWeyV" class="w-10 h-10 bg-enp-gold rounded-full flex items-center justify-center text-enp-dark hover:bg-white transition transform hover:scale-110">
            <svg xmlns="http://www.w3.org/2000/svg" class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24"><path d="M19.59 6.69a4.83 4.83 0 0 1-3.77-4.25V2h-3.45v13.67a2.89 2.89 0 0 1-5.2 1.74 2.89 2.89 0 0 1 2.31-4.64 2.93 2.93 0 0 1 .88.13V9.4a6.84 6.84 0 0 0-1-.05A6.33 6.33 0 0 0 5 22a6.34 6.34 0 0 0 10.86-4.43v-7a8.16 8.16 0 0 0 4.77 1.52v-3.4a4.85 4.85 0 0 1-1-.01z"/></svg>
          </a>
           <a href="https://www.instagram.com/enpgroup/" class="w-10 h-10 bg-enp-gold rounded-full flex items-center justify-center text-enp-dark hover:bg-white transition transform hover:scale-110">
             <svg xmlns="http://www.w3.org/2000/svg" class="w-5 h-5" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2"><rect x="2" y="2" width="20" height="20" rx="5" ry="5"></rect><path d="M16 11.37A4 4 0 1112.63 8 4 4 0 0116 11.37z"></path><line x1="17.5" y1="6.5" x2="17.51" y2="6.5"></line></svg>
          </a>
        </div>
      </div>

    </div>
    
    <div class="border-t border-gray-800 pt-8 text-center text-gray-400 text-sm relative">
      <p>&copy; {{ currentYear }} <span class="text-enp-gold font-semibold">ENP GROUP</span> | SainzLab.my.id</p>
    </div>
  </footer>
</template>
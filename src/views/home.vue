<template>
    <section
        class="relative h-screen bg-cover bg-no-repeat bg-[center_top_25%] flex items-center justify-center text-white"
        :style="{ backgroundImage: `url(${bgImage})` }"
    >
        <div class="absolute inset-0 bg-gradient-to-b from-black/50 via-black/30 to-black/60 backdrop-blur-[1px]"></div>
        
        <div class="relative text-center px-4 max-w-3xl z-10">
            <h1 class="text-5xl md:text-7xl font-extrabold tracking-tight mb-4 drop-shadow-lg uppercase">
                Welcome to Tembera u Rwanda
            </h1>
            <p class="text-xl md:text-2xl font-semibold text-green-400 drop-shadow-md tracking-wide">
                The Land of a Thousand Hills
            </p>
        </div>

        <div class="absolute bottom-6 left-1/2 -translate-x-1/2 animate-bounce opacity-75 hidden md:block">
            <svg class="w-6 h-6 text-white" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" d="M19.5 8.25l-7.5 7.5-7.5-7.5"></path>
            </svg>
        </div>
    </section>

    <section class="py-20 bg-gray-50">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="text-center mb-16">
                <h2 class="text-3xl md:text-4xl font-black text-gray-900 tracking-tight mb-3">
                    Explore Rwanda
                </h2>
                <div class="w-16 h-1 bg-green-500 mx-auto rounded-full"></div>
            </div>
            
            <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-8">
                <div
                    v-for="(card, idx) in cards"
                    :key="idx"
                    class="bg-white rounded-xl shadow-sm hover:shadow-xl transition-all duration-300 overflow-hidden flex flex-col group"
                >
                    <div class="w-full aspect-video overflow-hidden bg-gray-200 relative">
                        <img 
                            :src="card.img" 
                            :alt="card.title" 
                            class="w-full h-full object-cover object-center transform group-hover:scale-105 transition-transform duration-500 ease-out"
                            loading="lazy"
                        />
                    </div>
                    
                    <div class="p-6 flex-grow flex flex-col justify-between">
                        <div>
                            <h3 class="text-lg font-bold text-gray-800 mb-2 group-hover:text-green-600 transition-colors duration-200">
                                {{ card.title }}
                            </h3>
                            <p class="text-gray-600 text-sm leading-relaxed">
                                {{ card.text }}
                            </p>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>

<script setup>
import { ref } from 'vue'

// Hero Background Image (Your newly updated high-res river landscape)
const bgImage = new URL('../assets/Beautifull Nature.jpg', import.meta.url).href

// Destination Cards
const cards = ref([
    {
        title: 'Akagera National Park',
        text: 'Experience thrilling Big Five safaris and witness spectacular wildlife roaming open savannah plains.',
        img: new URL('../assets/akageraC.jpg', import.meta.url).href,
    },
    {
        title: 'Kigali City',
        text: 'Discover the vibrant capital with cultural, historical, and fine dining hotspots.',
        img: new URL('../assets/Rwanda.jpg', import.meta.url).href,
    },
    {
        title: 'Lake Kivu',
        text: 'Relax by the deep blue water, kayak, and enjoy scenic emerald island views.',
        img: new URL('../assets/Lake Kivu in Rwanda.jpg', import.meta.url).href,
    },
    {
        title: 'Nyungwe Canopy',
        text: 'Walk high among ancient treetops and spot rare primates in the pristine rainforest.',
        img: new URL('../assets/Canopy walk experience in Nyungwe Forest national park Rwanda.jpg', import.meta.url).href,
    },
])
</script>
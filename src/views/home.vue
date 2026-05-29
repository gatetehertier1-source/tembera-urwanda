<template>
    <!-- HERO SECTION -->
    <section
        class="relative h-screen bg-cover bg-no-repeat bg-[center_top_25%] flex items-center justify-center text-white overflow-hidden"
        :style="{ backgroundImage: `url(${bgImage})` }"
    >
        <!-- Overlay -->
        <div class="absolute inset-0 bg-gradient-to-b from-black/70 via-black/40 to-black/80"></div>

        <!-- Decorative Glow -->
        <div class="absolute top-20 left-10 w-72 h-72 bg-green-500/20 rounded-full blur-3xl"></div>
        <div class="absolute bottom-10 right-10 w-72 h-72 bg-emerald-400/10 rounded-full blur-3xl"></div>

        <!-- Hero Content -->
        <div class="relative text-center px-4 max-w-4xl z-10">
            <span
                class="inline-block px-4 py-1 mb-6 text-sm tracking-[0.3em] uppercase border border-white/30 rounded-full bg-white/10 backdrop-blur-md"
            >
                Discover Rwanda
            </span>

            <h1
                class="text-5xl sm:text-6xl md:text-7xl font-extrabold tracking-tight mb-5 drop-shadow-2xl uppercase leading-tight"
            >
                Welcome to <span class="text-green-400">Tembera u Rwanda</span>
            </h1>

            <p
                class="text-lg md:text-2xl font-medium text-gray-200 max-w-2xl mx-auto leading-relaxed"
            >
                Explore breathtaking landscapes, vibrant culture, wildlife adventures,
                and unforgettable experiences in the heart of Africa.
            </p>

            <!-- Buttons -->
            <div class="mt-10 flex flex-col sm:flex-row gap-4 justify-center">
                <button
                    class="px-8 py-3 bg-green-500 hover:bg-green-600 transition-all duration-300 rounded-full font-semibold shadow-lg hover:scale-105"
                >
                    Explore Now
                </button>

                <button
                    class="px-8 py-3 border border-white/40 bg-white/10 backdrop-blur-md hover:bg-white/20 transition-all duration-300 rounded-full font-semibold"
                >
                    Learn More
                </button>
            </div>
        </div>

        <!-- Scroll Indicator -->
        <div
            class="absolute bottom-6 left-1/2 -translate-x-1/2 animate-bounce opacity-75 hidden md:block"
        >
            <svg
                class="w-7 h-7 text-white"
                fill="none"
                stroke="currentColor"
                stroke-width="2"
                viewBox="0 0 24 24"
            >
                <path
                    stroke-linecap="round"
                    stroke-linejoin="round"
                    d="M19.5 8.25l-7.5 7.5-7.5-7.5"
                ></path>
            </svg>
        </div>
    </section>

    <!-- DESTINATIONS SECTION -->
    <section class="py-24 bg-gradient-to-b from-gray-50 to-white relative overflow-hidden">
        <!-- Background Decorations -->
        <div class="absolute -top-20 -left-20 w-80 h-80 bg-green-100 rounded-full blur-3xl opacity-40"></div>
        <div class="absolute bottom-0 right-0 w-96 h-96 bg-emerald-100 rounded-full blur-3xl opacity-30"></div>

        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 relative z-10">
            <!-- Section Header -->
            <div class="text-center mb-20">
                <span class="text-green-600 font-semibold uppercase tracking-[0.25em] text-sm">
                    Tourist Destinations
                </span>

                <h2
                    class="text-4xl md:text-5xl font-black text-gray-900 tracking-tight mt-3 mb-5"
                >
                    Explore Rwanda
                </h2>

                <p class="text-gray-600 max-w-2xl mx-auto leading-relaxed">
                    From breathtaking national parks to relaxing lakeside escapes,
                    Rwanda offers unforgettable adventures for every traveler.
                </p>

                <div class="w-20 h-1.5 bg-green-500 mx-auto rounded-full mt-6"></div>
            </div>

            <!-- Cards -->
            <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-8">
                <div
                    v-for="(card, idx) in cards"
                    :key="idx"
                    class="bg-white rounded-2xl shadow-md hover:shadow-2xl transition-all duration-500 overflow-hidden flex flex-col group border border-gray-100 hover:-translate-y-2"
                >
                    <!-- Image -->
                    <div class="w-full aspect-video overflow-hidden bg-gray-200 relative">
                        <img
                            :src="card.img"
                            :alt="card.title"
                            class="w-full h-full object-cover object-center transform group-hover:scale-110 transition-transform duration-700 ease-out"
                            loading="lazy"
                        />

                        <!-- Gradient Overlay -->
                        <div
                            class="absolute inset-0 bg-gradient-to-t from-black/50 via-transparent to-transparent opacity-70"
                        ></div>

                        <!-- Small Badge -->
                        <span
                            class="absolute top-4 left-4 bg-green-500 text-white text-xs px-3 py-1 rounded-full shadow-md"
                        >
                            Popular
                        </span>
                    </div>

                    <!-- Content -->
                    <div class="p-6 flex-grow flex flex-col justify-between">
                        <div>
                            <h3
                                class="text-xl font-bold text-gray-800 mb-3 group-hover:text-green-600 transition-colors duration-300"
                            >
                                {{ card.title }}
                            </h3>

                            <p class="text-gray-600 text-sm leading-relaxed">
                                {{ card.text }}
                            </p>
                        </div>

                        <!-- Button -->
                        <button
                            class="mt-6 text-green-600 font-semibold flex items-center gap-2 group-hover:gap-3 transition-all duration-300"
                        >
                            Discover
                            <svg
                                class="w-4 h-4"
                                fill="none"
                                stroke="currentColor"
                                stroke-width="2"
                                viewBox="0 0 24 24"
                            >
                                <path
                                    stroke-linecap="round"
                                    stroke-linejoin="round"
                                    d="M9 5l7 7-7 7"
                                ></path>
                            </svg>
                        </button>
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>

<script setup>
import { ref } from 'vue'

// Hero Background Image
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
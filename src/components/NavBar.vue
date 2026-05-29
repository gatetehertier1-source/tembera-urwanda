<script setup>
import { ref } from 'vue'
import { RouterLink, RouterView } from 'vue-router'
import { useTranslator } from '../composables/useTranslator'

const isGalleryOpen = ref(false)
const isDestinationOpen = ref(false)
const isLanguageOpen = ref(false)
const { t, setLanguage, languages, state } = useTranslator()

const selectLanguage = (code) => {
  setLanguage(code)
  isLanguageOpen.value = false
}
</script>

<template>
  <div class="min-h-screen flex flex-col bg-gray-50">
    <nav class="bg-green-800 text-white px-8 py-4 flex items-center justify-between shadow-md relative">
      <div class="flex items-center gap-3">
        <img src="../assets/sos1.svg" class="h-8 w-8" alt="Logo" />
      </div>

      <div class="flex items-center gap-10">
        <ul class="flex gap-10 items-center justify-end font-medium">
          <li>
            <RouterLink to="/" class="nav-link">{{ t('nav_home') }}</RouterLink>
          </li>

          <li>
            <RouterLink to="/about" class="nav-link">{{ t('nav_about') }}</RouterLink>
          </li>

          <li>
            <RouterLink to="/services" class="nav-link">{{ t('nav_services') }}</RouterLink>
          </li>

          <li
            class="relative cursor-pointer py-2"
            @mouseenter="isGalleryOpen = true"
            @mouseleave="isGalleryOpen = false"
          >
            <span class="nav-link">
              {{ t('nav_gallery') }}
              <span
                class="text-xs transition-transform duration-200"
                :class="{ 'rotate-180 text-yellow-300': isGalleryOpen }"
              >
                ▼
              </span>
            </span>

            <div v-if="isGalleryOpen" class="absolute left-0 top-full pt-2 w-48 z-50">
              <ul class="bg-white text-green-900 rounded shadow-lg py-2 border border-gray-100">
                <li>
                  <RouterLink to="/gallery/photos" class="dropdown-link">{{ t('nav_photos') }}</RouterLink>
                </li>
                <li>
                  <RouterLink to="/gallery/videos" class="dropdown-link">{{ t('nav_videos') }}</RouterLink>
                </li>
              </ul>
            </div>
          </li>

          <li
            class="relative cursor-pointer py-2"
            @mouseenter="isDestinationOpen = true"
            @mouseleave="isDestinationOpen = false"
          >
            <span class="nav-link">
              {{ t('nav_destination') }}
              <span
                class="text-xs transition-transform duration-200"
                :class="{ 'rotate-180 text-yellow-300': isDestinationOpen }"
              >
                ▼
              </span>
            </span>

            <div v-if="isDestinationOpen" class="absolute left-0 top-full pt-2 w-48 z-50">
              <ul class="bg-white text-green-900 rounded shadow-lg py-2 border border-gray-100">
                <li>
                  <RouterLink to="/dest/northern" class="dropdown-link">Northern</RouterLink>
                </li>
                <li>
                  <RouterLink to="/dest/southern" class="dropdown-link">Southern</RouterLink>
                </li>
                <li>
                  <RouterLink to="/dest/eastern" class="dropdown-link">Eastern</RouterLink>
                </li>
                <li>
                  <RouterLink to="/dest/western" class="dropdown-link">Western</RouterLink>
                </li>
                <li>
                  <RouterLink to="/dest/kigali" class="dropdown-link">Kigali</RouterLink>
                </li>
              </ul>
            </div>
          </li>

          <li>
            <RouterLink to="/contacts" class="nav-link">{{ t('nav_contacts') }}</RouterLink>
          </li>
        </ul>

        <div class="relative">
          <button
            class="rounded-md border border-white/30 bg-white/10 px-3 py-2 text-sm text-white transition hover:bg-white/15"
            @click="isLanguageOpen = !isLanguageOpen"
            type="button"
          >
            {{ t('translator') }}
          </button>

          <div
            v-if="isLanguageOpen"
            class="absolute right-0 mt-2 w-48 rounded-xl bg-white text-slate-900 shadow-lg ring-1 ring-black/10"
          >
            <div class="px-4 py-3 border-b border-slate-200 text-sm text-slate-700">
              {{ t('select_language') }}
            </div>
            <ul>
              <li
                v-for="language in languages"
                :key="language.code"
                class="cursor-pointer px-4 py-2 hover:bg-slate-100"
                @click="selectLanguage(language.code)"
              >
                {{ t(language.labelKey) }}
                <span v-if="state.lang === language.code" class="text-sm text-green-600"> ✓</span>
              </li>
            </ul>
          </div>
        </div>
      </div>
    </nav>

    <main class="p-8 flex-grow">
      <RouterView />
    </main>
  </div>
</template>

<style scoped>
.nav-link {
  display: inline-flex;
  align-items: center;
  gap: 0.25rem;
  transition: color 150ms ease;
  color: white;
}

.nav-link:hover {
  color: #fde047; /* tailwind yellow-300 */
}

.dropdown-link {
  display: block;
  padding: 0.5rem 1rem; /* px-4 py-2 */
  transition: background-color 150ms ease, color 150ms ease;
  color: #064e3b; /* green-900 */
}

.dropdown-link:hover {
  background-color: #fef9c3; /* yellow-50 */
  color: #b45309; /* yellow-700 */
}
</style>


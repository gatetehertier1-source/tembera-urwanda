<script setup>
import { useTranslator } from '../../composables/useTranslator'

const { t } = useTranslator()

const photos = [
  {
    src: new URL('../../assets/Lake Kivu in Rwanda.jpg', import.meta.url).href,
    captionKey: 'photo_caption_1',
  },
  {
    src: new URL('../../assets/mukera.jpg', import.meta.url).href,
    captionKey: 'photo_caption_2',
  },
  {
    src: new URL('../../assets/Rwanda.jpg', import.meta.url).href,
    captionKey: 'photo_caption_3',
  },
  {
    src: new URL('../../assets/sena.jpg', import.meta.url).href,
    captionKey: 'photo_caption_4',
  },
  {
    src: new URL('../../assets/tembera.jpg', import.meta.url).href,
    captionKey: 'photo_caption_5',
  },
]
</script>

<template>
  <section class="space-y-8">
    <div class="text-center">
      <h1 class="text-4xl font-bold mb-3">{{ t('photos_title') }}</h1>
      <p class="mx-auto max-w-3xl text-slate-600">{{ t('photos_intro') }}</p>
    </div>

    <div class="grid gap-6 sm:grid-cols-2 lg:grid-cols-3">
      <article
        v-for="(photo, index) in photos"
        :key="index"
        class="overflow-hidden rounded-3xl bg-white shadow-lg"
      >
        <img :src="photo.src" :alt="t(photo.captionKey)" class="h-64 w-full object-cover" />
        <div class="p-5">
          <p class="font-semibold text-slate-900">{{ t(photo.captionKey) }}</p>
        </div>
      </article>
    </div>
  </section>
</template>
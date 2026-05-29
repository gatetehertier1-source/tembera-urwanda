<script setup>
import { useTranslator } from '../../composables/useTranslator'

const { t } = useTranslator()

const videos = [
  {
    titleKey: 'video_caption_1',
    description: 'A short safari highlight reel from eastern Rwanda.',
    src: 'https://interactive-examples.mdn.mozilla.net/media/cc0-videos/flower.mp4',
  },
  {
    titleKey: 'video_caption_2',
    description: 'A city culture clip with market and food scenes.',
    src: 'https://interactive-examples.mdn.mozilla.net/media/cc0-videos/flower.mp4',
  },
  {
    titleKey: 'video_caption_3',
    description: 'Lake views with relaxing water and sunset footage.',
    src: 'https://interactive-examples.mdn.mozilla.net/media/cc0-videos/flower.mp4',
  },
]
</script>

<template>
  <section class="space-y-8">
    <div class="text-center">
      <h1 class="text-4xl font-bold mb-3">{{ t('videos_title') }}</h1>
      <p class="mx-auto max-w-3xl text-slate-600">{{ t('videos_intro') }}</p>
    </div>

    <div class="grid gap-6 lg:grid-cols-3">
      <article
        v-for="(video, index) in videos"
        :key="index"
        class="overflow-hidden rounded-3xl bg-white shadow-lg"
      >
        <div class="relative overflow-hidden bg-slate-900">
          <video
            class="h-56 w-full object-cover"
            controls
            muted
            preload="metadata"
          >
            <source :src="video.src" type="video/mp4" />
            {{ t('videos_intro') }}
          </video>
        </div>
        <div class="p-5">
          <h2 class="text-xl font-semibold mb-2">{{ t(video.titleKey) }}</h2>
          <p class="text-slate-600">{{ video.description }}</p>
        </div>
      </article>
    </div>
  </section>
</template>
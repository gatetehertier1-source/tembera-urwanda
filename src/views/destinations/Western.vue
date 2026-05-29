<script setup>
import { useTranslator } from '../../composables/useTranslator'

const { t } = useTranslator()
const image = new URL('../../assets/Lake Kivu in Rwanda.jpg', import.meta.url).href
const features = [
  { titleKey: 'western_feature_1' },
  { titleKey: 'western_feature_2' },
  { titleKey: 'western_feature_3' },
]
</script>

<template>
  <section class="space-y-10">
    <div class="grid gap-8 lg:grid-cols-[1.3fr_1fr] items-center">
      <div>
        <h1 class="text-4xl font-bold mb-4">{{ t('western_title') }}</h1>
        <p class="text-slate-700 text-lg">{{ t('western_description') }}</p>
      </div>
      <img :src="image" alt="Western Rwanda" class="rounded-3xl shadow-xl w-full object-cover h-96" />
    </div>

    <div class="grid gap-6 md:grid-cols-3">
      <article
        v-for="(feature, index) in features"
        :key="index"
        class="rounded-3xl border border-slate-200 bg-white p-6 shadow-sm"
      >
        <h2 class="text-xl font-semibold mb-3">{{ t(feature.titleKey) }}</h2>
        <p class="text-slate-600">{{ t('western_description') }}</p>
      </article>
    </div>
  </section>
</template>
<script setup>
import BadgeDomain from "./BadgeDomain.vue";

const IMG_BASE_URL = "../../../public/assets/";

const props = defineProps({
  title: String,
  domain: String,
  long_description: String,
  features: Array,
  steps: Array,
  result: String,
  tools: Array,
  dev_languages: Array,
});
</script>

<template>
  <div
    class="relative w-screen h-screen bg-white flex flex-col overflow-y-auto p-12"
    style="max-width: 100vw; max-height: 100vh"
  >
    <!-- Titre centré en haut -->
    <h2 class="text-3xl font-bold text-gray-900 mb-4 text-center tracking-wide">
      {{ title }}
    </h2>

    <!-- Badge domaine -->
    <div class="mb-4 flex justify-center">
      <BadgeDomain :label="domain"></BadgeDomain>
    </div>

    <!-- Ligne de séparation -->
    <div class="h-1 bg-gray-300 mb-4"></div>

    <!-- Description longue -->
    <p class="text-gray-700 text-sm mb-6 text-center leading-relaxed">
      {{ long_description }}
    </p>

    <!-- Features -->
    <div v-if="features && features.length" class="mb-6 w-full">
      <ul class="space-y-0 flex flex-col items-center">
        <li
          v-for="(feature, index) in features"
          :key="feature.title"
          :class="[
            'flex flex-col md:flex-row gap-3 max-w-3xl items-center w-full px-2 md:px-0',
            index % 2 === 1 ? 'md:flex-row-reverse' : '',
          ]"
        >
          <!-- Image -->
          <img
            :src="IMG_BASE_URL + feature.image"
            :alt="'Mockup'"
            :style="{
              height: 'clamp(10vh, 30vh, 60vh)',
              width: 'auto',
              transform: index % 2 === 0 ? 'rotate(-2deg)' : 'rotate(2deg)',
            }"
            class="object-contain flex-shrink-0 w-full md:w-auto"
          />
          <!-- Texte -->
          <div class="flex-1 px-4 md:px-6 py-4 w-full md:w-auto">
            <h4 class="text-lg font-bold text-gray-900 mb-2 text-center">
              {{ feature.title }}
            </h4>
            <p class="text-gray-600 text-sm leading-relaxed text-center">
              {{ feature.description }}
            </p>
          </div>
        </li>
      </ul>
    </div>

    <!-- Étapes -->
    <div v-if="steps && steps.length" class="mb-6">
      <p class="text-gray-900 text-sm font-semibold mb-2">DÉMARCHE</p>
      <ol class="space-y-2">
        <li
          v-for="(step, index) in steps"
          :key="step"
          class="text-gray-700 text-sm"
        >
          {{ index + 1 }}. {{ step }}
        </li>
      </ol>
    </div>

    <!-- Résultat -->
    <div v-if="result" class="mb-6 p-4 bg-gray-100 rounded">
      <h3 class="text-lg font-bold text-gray-900 mb-2">Résultat</h3>
      <p class="text-gray-700 text-sm">{{ result }}</p>
    </div>

    <!-- Outils -->
    <div v-if="tools && tools.length" class="mb-4">
      <p class="text-gray-900 text-sm font-semibold mb-2">OUTILS</p>
      <div class="flex flex-wrap gap-2">
        <span
          v-for="tool in tools"
          :key="tool"
          class="bg-red-500 text-white px-3 py-1 rounded text-sm font-semibold"
        >
          {{ tool }}
        </span>
      </div>
    </div>

    <!-- Technologies -->
    <div v-if="dev_languages && dev_languages.length">
      <p class="text-gray-900 text-sm font-semibold mb-2">TECHNOLOGIES</p>
      <div class="flex flex-wrap gap-2">
        <span
          v-for="lang in dev_languages"
          :key="lang"
          class="bg-gray-900 text-white px-3 py-1 rounded text-sm font-semibold"
        >
          {{ lang }}
        </span>
      </div>
    </div>
  </div>
</template>

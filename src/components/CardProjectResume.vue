<script setup>
import BadgeDomain from "./BadgeDomain.vue";

const props = defineProps({
  title: String,
  domain: String,
  cover_image: String,
  short_description: String,
  tools: Array,
  dev_languages: Array,
});
</script>

<template>
  <div
    class="relative w-60 h-80 bg-white rounded-2xl p-5 shadow-lg border-3 border-gray-800 hover:shadow-2xl transition-all duration-300 hover:scale-105 cursor-pointer flex flex-col"
  >
    <!-- Titre centré en haut -->
    <h2 class="text-1xl font-bold text-gray-900 mb-2 text-center tracking-wide">
      {{ title }}
    </h2>

    <!-- Image de couverture -->
    <img
      :src="cover_image"
      :alt="'Mockup du projet'"
      class="w-full h-60 object-cover rounded mb-2"
    />

    <!-- Badge domaine -->
    <div class="mb-3 flex justify-center">
      <BadgeDomain :label="domain"></BadgeDomain>
    </div>

    <!-- Description -->
    <p class="text-gray-700 text-xs mb-3 text-center leading-relaxed flex-grow">
      {{ short_description }}
    </p>
  </div>
</template>

<script setup>
import BadgeDomain from "./BadgeDomain.vue";
import { computed } from "vue";

const props = defineProps({
  title: String,
  domain: String,
  cover_image: String,
  short_description: String,
  tools: Array,
  dev_languages: Array,
});

const domainClass = computed(() => {
  if (props.domain === "UX/UI") return "uxui";
  if (props.domain === "Développement") return "dev";
  if (props.domain === "Design graphique") return "design";
  return "uxui"; // classe par défaut si aucun match
});
</script>

<template>
  <div
    :class="[
      domainClass,
      'relative w-60 h-80 rounded-xl p-2 shadow-lg hover:shadow-2xl transition-all duration-300 hover:scale-105 cursor-pointer flex flex-col',
    ]"
  >
    <!-- Image de couverture -->
    <img
      :src="cover_image"
      :alt="'Mockup du projet'"
      class="w-full h-60 object-cover mb-2"
    />

    <div class="bg-white bg-opacity-50">
      <!-- Titre centré en haut -->
      <h2
        class="text-1xl font-bold text-gray-900 mb-2 text-center tracking-wide"
      >
        {{ title }}
      </h2>

      <!-- Description -->
      <p
        class="text-gray-700 text-xs mb-3 text-center leading-relaxed flex-grow"
      >
        {{ short_description }}
      </p>
    </div>
  </div>
</template>

<style>
.uxui {
  background-color: #023059;
}
.dev {
  background-color: #4e6e4b;
}
.design {
  background-color: #cda438;
}
</style>

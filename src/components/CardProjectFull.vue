<script setup>
import BadgeDomain from "./BadgeDomain.vue";

const props = defineProps({
  title: String,
  domain: String,
  description: String,
  features: Array,
  steps: Array,
  result: String,
  tools: Array,
  dev_languages: Array,
});
</script>

<template>
  <h1>{{ title }}</h1>
  <BadgeDomain :label="domain"></BadgeDomain>
  <p>{{ description }}</p>
  <li v-for="feature in features">
    {{ feature }}
  </li>
  <li v-for="step in steps">
    {{ step }}
  </li>
  <p>{{ result }}</p>
  <li v-for="tool in tools">
    {{ tool }}
  </li>
  <li v-for="dev_language in dev_languages">
    {{ dev_language }}
  </li>
</template>

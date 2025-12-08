<script setup>
import ChipSkill from "./ChipSkill.vue";

const props = defineProps({
  title: String,
  skill: String,
  description: String,
  features: Array,
  steps: Array,
  result: String,
  technologies: Array,
});
</script>

<template>
  <h1>{{ title }}</h1>
  <ChipSkill :label="skill"></ChipSkill>
  <p>{{ description }}</p>
  <li v-for="feature in features">
    {{ feature }}
  </li>
</template>

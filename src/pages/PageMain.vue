<script setup>
import CardProject from "../components/CardProject.vue";
import all-projects from "../../data/projects.json"
</script>

<template>
  <h1>Mon portfolio</h1>

  <li>
    <CardProject :title="'Naturaquest'" :skill="'UXUI'"></CardProject>
  </li>
</template>

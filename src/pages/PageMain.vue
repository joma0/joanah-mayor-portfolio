<script setup>
import CardProjectFull from "../components/CardProjectFull.vue";
import CardProjectResume from "../components/CardProjectResume.vue";
import projects from "../../data/projects.json";
</script>

<template>
  <h1>Mon portfolio</h1>

  <li v-for="project in projects" :key="project.title">
    <CardProjectResume
      :title="project.title"
      :domain="project.domain"
      :description="project.description"
      :tools="project.tools"
      :dev_languages="project.dev_languages"
    ></CardProjectResume>
  </li>

  <li v-for="project in projects" :key="project.title">
    <CardProjectFull
      :title="project.title"
      :domain="project.domain"
      :description="project.description"
      :features="project.features"
      :steps="project.steps"
      :result="project.result"
      :tools="project.tools"
      :dev_languages="project.dev_languages"
    ></CardProjectFull>
  </li>
</template>

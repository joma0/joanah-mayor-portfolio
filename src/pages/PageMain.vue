<script setup>
import CardProject from "../components/CardProject.vue";
import projects from "../../data/projects.json";
</script>

<template>
  <h1>Mon portfolio</h1>

  <li v-for="project in projects" :key="project.title">
    <CardProject
      :title="project.title"
      :domain="project.domain"
      :description="project.description"
      :features="project.features"
      :steps="project.steps"
      :result="project.result"
      :tools="project.tools"
      :dev_languages="project.dev_languages"
    ></CardProject>
  </li>
</template>

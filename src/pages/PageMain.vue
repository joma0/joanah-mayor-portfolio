<script setup>
import CardProjectFull from "../components/CardProjectFull.vue";
import CardProjectResume from "../components/CardProjectResume.vue";
import projects from "../../data/projects.json";

const IMG_BASE_URL = "../../../public/assets/";
</script>

<template>
  <div class="wood-background min-h-screen">
    <h1>Mon portfolio</h1>

    <div
      class="grid p-4"
      style="
        grid-template-columns: repeat(auto-fit, minmax(18rem, 1fr));
        column-gap: 1rem;
        row-gap: 1rem;
      "
    >
      <div v-for="project in projects" :key="project.title">
        <CardProjectResume
          :title="project.title"
          :domain="project.domain"
          :cover_image="IMG_BASE_URL + project.cover_image"
          :short_description="project.short_description"
          :tools="project.tools"
          :dev_languages="project.dev_languages"
        ></CardProjectResume>
      </div>
    </div>

    <li v-for="project in projects" :key="project.title">
      <CardProjectFull
        :title="project.title"
        :domain="project.domain"
        :long_description="project.long_description"
        :features="project.features"
        :steps="project.steps"
        :result="project.result"
        :tools="project.tools"
        :dev_languages="project.dev_languages"
      ></CardProjectFull>
    </li>
  </div>
</template>

<style scoped>
.wood-background {
  background: linear-gradient(135deg, #8b6f47 0%, #9b7f57 50%, #8b6f47 100%);
  position: relative;
}

.wood-background::before {
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-image: repeating-linear-gradient(
      25deg,
      transparent,
      transparent 30px,
      rgba(0, 0, 0, 0.05) 30px,
      rgba(0, 0, 0, 0.05) 31px
    ),
    repeating-linear-gradient(
      -35deg,
      transparent,
      transparent 40px,
      rgba(0, 0, 0, 0.04) 40px,
      rgba(0, 0, 0, 0.04) 41px
    ),
    repeating-linear-gradient(
      55deg,
      transparent,
      transparent 50px,
      rgba(0, 0, 0, 0.03) 50px,
      rgba(0, 0, 0, 0.03) 51px
    );
  pointer-events: none;
}

.wood-background > * {
  position: relative;
  z-index: 1;
}
</style>

<script setup>
import CardProjectFull from "../components/CardProjectFull.vue";
import CardProjectResume from "../components/CardProjectResume.vue";
import projects from "../../data/projects.json";
import { ref } from "vue";

const IMG_BASE_URL = "../../../public/assets/";
const selectedProject = ref(null);

const openProject = (project) => {
  selectedProject.value = project;
};

const closeProject = () => {
  selectedProject.value = null;
};
</script>

<template>
  <div class="bg-[#E6D3B5] min-h-screen flex flex-col items-center">
    <h1 class="text-5xl font-bold text-gray-900 text-center py-8 w-full">
      Mon portfolio
    </h1>

    <div
      class="grid p-4 md:p-12 lg:p-16 max-w-7xl w-full"
      style="
        grid-template-columns: repeat(auto-fit, minmax(18rem, 1fr));
        column-gap: 1rem;
        row-gap: 1rem;
      "
    >
      <div
        v-for="project in projects"
        :key="project.title"
        @click="openProject(project)"
      >
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
  </div>

  <!-- Overlay modal en dehors du wood-background -->
  <div
    v-if="selectedProject"
    class="fixed inset-0 flex items-center justify-center"
    style="z-index: 9999; background-color: rgba(0, 0, 0, 0.7)"
    @click="closeProject"
  >
    <div class="relative" @click.stop>
      <button
        class="absolute top-4 right-4 text-white bg-gray-900 hover:bg-gray-700 rounded-full w-10 h-10 flex items-center justify-center"
        style="z-index: 10000"
        @click="closeProject"
      >
        ✕
      </button>
      <CardProjectFull
        :title="selectedProject.title"
        :domain="selectedProject.domain"
        :long_description="selectedProject.long_description"
        :features="selectedProject.features"
        :steps="selectedProject.steps"
        :results="selectedProject.result"
        :tools="selectedProject.tools"
        :dev_languages="selectedProject.dev_languages"
      ></CardProjectFull>
    </div>
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

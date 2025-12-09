<script setup>
import CardProjectFull from "../components/CardProjectFull.vue";
import CardProjectResume from "../components/CardProjectResume.vue";
import BadgeDomain from "../components/BadgeDomain.vue";
import projects from "../../data/projects.json";
import { ref } from "vue";

const IMG_BASE_URL = "/assets/";
const selectedProject = ref(null);

const openProject = (project) => {
  selectedProject.value = project;
};

const closeProject = () => {
  selectedProject.value = null;
};
</script>

<template>
  <div class="bg-[#E6D3B5] min-h-screen flex flex-col items-center py-8">
    <div class="retro-frame p-8 max-w-3xl mx-auto text-center space-y-4">
      <h1 class="text-5xl font-bold text-gray-900 text-center py-2 w-full">
        Joanah Mayor
      </h1>
      <p>Actuellement en 3e année d'ingénierie des médias à la HEIG-VD.</p>
      <p>J'aime le dev et le design, et un mélange des deux c'est l'idéal.</p>
    </div>

    <h2 class="text-3xl font-bold text-gray-900 text-center py-8 w-full">
      Mes projets
    </h2>

    <!-- Badge domaine -->
    <div class="mb-3 flex justify-center gap-4">
      <BadgeDomain :label="'UX/UI'" class="uxui"></BadgeDomain>
      <BadgeDomain :label="'Développement'" class="dev"></BadgeDomain>
      <BadgeDomain :label="'Design graphique'" class="design"></BadgeDomain>
    </div>

    <div
      class="grid p-4 md:p-4 lg:px-48 max-w-7xl w-full gap-6 grid-cols-1 md:grid-cols-2 lg:grid-cols-3 mx-auto"
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

.retro-frame {
  border: 4px solid #8b4513; /* bordure brun chocolat */
  border-radius: 16px; /* coins arrondis */
  box-shadow: 4px 4px 0px #d2b48c; /* effet relief façon plateau de jeu */
  background: #fdf5e6; /* fond “vieux papier” */
  position: relative;
}

.retro-frame::before {
  content: "";
  position: absolute;
  top: 8px;
  left: 8px;
  right: 8px;
  bottom: 8px;
  border: 2px dashed #8b4513; /* bordure intérieure en pointillé */
  pointer-events: none;
  border-radius: 12px;
}
</style>

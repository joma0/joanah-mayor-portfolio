<script setup>
const props = defineProps({
  label: String,
});
</script>
<template>
  <span
    class="inline-block px-3 py-1 bg-blue-500 text-white rounded-full text-sm font-medium"
  >
    {{ label }}
  </span>
</template>

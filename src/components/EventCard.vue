<script setup>
defineProps({
  title: String,
  when: String,
  description: String,
});
</script>

<template>
  <div class="border border-gray-800 bg-white rounded-md">
    <h2 class="text-xl p-4 border-b border-gray-400 font-medium">
      {{ title }}
    </h2>
    <p class="p-4 border-b border-gray-400">{{ when }}</p>
    <p class="p-4">{{ description }}</p>
  </div>
</template>

<script setup>
defineProps({
  title: String,
  when: String,
  description: String,
});

defineEmits(["register"]);
</script>

<template>
  <div class="border border-gray-800 bg-white rounded-md">
    <h2 class="text-xl p-4 border-b border-gray-400 font-medium">
      {{ title }}
    </h2>
    <p class="p-4 border-b border-gray-400">{{ when }}</p>
    <p class="p-4">{{ description }}</p>
    <section class="flex justify-end p-4">
      <button
        class="border border-gray-400 rounded-full px-3 py-1 hover:bg-gray-200"
        @click="$emit('register')"
      >
        Register
      </button>
    </section>
  </div>
</template>

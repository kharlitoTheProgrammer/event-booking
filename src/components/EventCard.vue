<template>
  <SectionCard>
    <template #header>
      <h3>{{ title }}</h3>
    </template>

    {{ when }}

    <template #footer>
      <div class="space-y-4">
        <p>{{ description }}</p>
        <div class="flex justify-end">
          <RoundButton @click="$emit('register')">Register</RoundButton>
        </div>
      </div>
    </template>
  </SectionCard>
</template>

<script setup>
import RoundButton from "./RoundButton.vue";
import SectionCard from "./SectionCard.vue";

defineProps({
  title: String,
  when: String,
  description: String,
});

defineEmits(["register"]);
</script>

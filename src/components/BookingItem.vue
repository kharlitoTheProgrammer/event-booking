<template>
  <SectionCard>
    <div class="flex justify-between">
      <div>{{ title }}</div>
      <RoundButton variant="danger">Cancel</RoundButton>
    </div>
  </SectionCard>
</template>

<script setup>
import RoundButton from "@/components/RoundButton.vue";
import SectionCard from "@/components/SectionCard.vue";

defineProps({
  title: String,
});
</script>

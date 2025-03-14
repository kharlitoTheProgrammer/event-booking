<template>
  <RoundedCard>
    <h3 class="text-xl p-4 border-b border-gray-400 font-medium">
      <slot name="header"></slot>
    </h3>

    <div class="p-4 border-b border-gray-400">
      <slot></slot>
    </div>

    <div class="p-4">
      <slot name="footer"></slot>
    </div>
  </RoundedCard>
</template>

<script setup lang="ts">
import RoundedCard from "@/components/RoundedCard.vue";
</script>

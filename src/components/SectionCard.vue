<template>
  <RoundedCard>
    <h3
      v-if="$slots.header"
      class="text-xl p-4 border-b border-gray-400 font-medium"
    >
      <slot name="header"></slot>
    </h3>

    <div
      v-if="$slots.default"
      :class="{ 'p-4': true, 'border-b border-gray-400': $slots.footer }"
    >
      <slot></slot>
    </div>

    <div v-if="$slots.footer" class="p-4">
      <slot name="footer"></slot>
    </div>
  </RoundedCard>
</template>

<script setup>
import RoundedCard from "@/components/RoundedCard.vue";
</script>

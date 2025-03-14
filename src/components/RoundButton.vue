<template>
  <button
    :class="[
      'text-sm font-medium rounded-full px-3 py-1',
      variants[variant] ?? variants.default,
    ]"
    @click="$emit('click')"
  >
    <slot></slot>
  </button>
</template>

<script setup>
const variants = {
  default: "border border-gray-200 hover:bg-gray-200",
  danger: "bg-red-200 enabled:hover:bg-red-100 text-red-900",
  primary: "bg-blue-500 hover:bg-blue-400 text-white",
};
defineProps({
  variant: String,
});
defineEmits(["click"]);
</script>

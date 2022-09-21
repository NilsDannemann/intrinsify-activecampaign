<script lang="ts" setup>
defineProps({
  text: {
    type: String,
    default: '',
  },
})
</script>

<template>
  <div class="text-4xl font-semibold">
    <slot>{{ text }}</slot>
  </div>
</template>

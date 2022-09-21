<script lang="ts" setup>
defineProps({
  text: {
    type: String,
    default: '',
  },
})
</script>

<template>
  <div class="text-xl font-semibold px-6 pb-0 pt-6 mb-2">
    <slot>{{ text }}</slot>
  </div>
</template>

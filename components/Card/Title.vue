<script lang="ts" setup>
defineProps({
  text: {
    type: String,
    default: '',
  },
})
</script>

<template>
  <div class="text-xl font-extrabold px-6 pt-4 pb-4">
    <slot>{{ text }}</slot>
  </div>
</template>

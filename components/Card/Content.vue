<script lang="ts" setup>
  defineProps({
    text: {
      type: String,
      default: '',
    },
  })
</script>

<template>
  <div class="card-content px-6 pb-4 relative">
    <slot>{{ text }}</slot>
  </div>
</template>

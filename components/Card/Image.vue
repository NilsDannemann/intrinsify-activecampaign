<script lang="ts" setup>
  defineProps({
    src: {
      type: String,
      default: '',
    },
  })
  </script>

<template>
  <div class="h-40 mb-4 bg-cover bg-center" v-bind:style="{ 'background-image': 'url(' + src + ')' }"></div>
</template>

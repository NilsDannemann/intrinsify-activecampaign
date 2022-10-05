<script lang="ts" setup>
import { capitalize } from '~/utils/str'

// composable
const { t } = useLang()

// compiler macro
definePageMeta({
  layout: 'blank',
})
useHead(() => ({
  title: 'Authentication',
}))
</script>

<template>
  <PageWrapper class="flex flex-col items-center justify-center">
    Auth here
  </PageWrapper>
</template>

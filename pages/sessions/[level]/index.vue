<script lang="ts" setup>
  // helpers
  import { capitalize } from '~/utils/str'

  const { t } = useLang()
  
  // router
  const route = useRoute()
  
  // data
  const { data: sessions } = await useFetch('http://localhost:3004/sessions')
  
  // layout
  definePageMeta({
    layout: 'page',
  })
  useHead(() => ({
    title: capitalize(route.params.level) + ' Level',
    meta: [
      {
        name: 'description',
        content: route.params.level + ' Level',
      },
    ],
  }))
</script>
  
<template>
  <PageWrapper>
    <PageHeader>
      <PageTitle text="Level" />
    </PageHeader>
    <PageBody>
      <PageSection>
        <p>Route params: {{ route.params }}</p>
      </PageSection>
    </PageBody>
  </PageWrapper>
</template>
  
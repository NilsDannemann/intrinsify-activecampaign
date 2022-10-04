<script lang="ts" setup>
import { capitalize } from '~/utils/str'

// sample API
const { data: sessions } = await useFetch('http://localhost:3004/sessions', { initialCache: false })

// composable
const { t } = useLang()

// compiler macro
definePageMeta({
  layout: 'page',
})
useHead(() => ({
  title: capitalize(t('pages.about.title')),
  meta: [
    {
      name: 'description',
      content: t('pages.about.description'),
    },
  ],
}))
</script>

<template>
  <PageWrapper>
    <PageHeader>
      <PageTitle :text="$t('pages.about.title')" />
    </PageHeader>
    <PageBody>
      <PageSection>
        About Page
      </PageSection>
    </PageBody>
  </PageWrapper>
</template>

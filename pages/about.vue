<script lang="ts" setup>
import { capitalize } from '~/utils/str'

// sample API
const { data: sessions } = await useFetch('http://localhost:3004/sessions')

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
        <div class="grid lg:grid-cols-4 md:grid-cols-3 sm:grid-cols-1 gap-6">
          <div v-for="session in sessions">
            <Card>
              <Card-Title :text="session.title" />
              <Card-Image :src="session.image" />
              <Card-Content :text="session.description" />
              <Card-Footer>ID: {{ session.id }}</Card-Footer>
            </Card>
          </div>
        </div>
      </PageSection>
    </PageBody>
  </PageWrapper>
</template>

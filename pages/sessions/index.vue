<script lang="ts" setup>
  // helpers
  import { capitalize } from '~/utils/str'
  
  // composables
  const { t } = useLang()
  
  // router
  const route = useRoute()
  
  // data
  const { data: level } = await useFetch('http://localhost:3004/level')
  // const level = ref({})
  // onMounted(async () => {
  //     level.value = await fetch('http://localhost:3004/level/').then(response => response.json()).catch(error => console.error(error))
  // })

  // layout
  definePageMeta({
    layout: 'page',
  })
  useHead(() => ({
    title: capitalize(t('pages.sessions.title')),
    meta: [
      {
        name: 'description',
        content: t('pages.sessions.description'),
      },
    ],
  }))
</script>
  
<template>
  <PageWrapper>
    <PageHeader>
      <PageTitle :text="$t('pages.sessions.title')" />
    </PageHeader>
    <PageBody>
      <PageSection>
        <p>Route params: {{ route.params }}</p>
        <div class="grid lg:grid-cols-4 md:grid-cols-3 sm:grid-cols-1 gap-6">
          <div v-for="level in level">
            <Anchor :to="'sessions/' + level.slug">
              <Card>
                <Card-Title :text="level.title" />
                <Card-Image :src="level.image" />
                <Card-Content :text="level.description" />
                <Card-Footer>ID: {{ level.id }}</Card-Footer>
              </Card>
            </Anchor>
          </div>
        </div>
      </PageSection>
    </PageBody>
  </PageWrapper>
</template>
  
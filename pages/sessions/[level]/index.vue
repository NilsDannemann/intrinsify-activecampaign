<script lang="ts" setup>
  // helpers
  import { capitalize } from '~/utils/str'

  // composables
  const { t } = useLang()
  
  // router
  const route = useRoute()
  
  // data
  const { data: sessions } = await useFetch('http://localhost:3004/sessions', { initialCache: false })
  // const sessions = ref({})
  // onMounted(async () => {
  //     sessions.value = await fetch('http://localhost:3004/sessions/').then(response => response.json()).catch(error => console.error(error))
  // })

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
      <PageTitle :text="route.params.level" />
    </PageHeader>
    <PageBody>
      <PageSection>
        <p>Route params: {{ route.params }}</p>
        <div class="grid lg:grid-cols-4 md:grid-cols-3 sm:grid-cols-1 gap-6">
          <div v-for="session in sessions">
            <Anchor :to="'/sessions/' + route.params.level + '/' + session.id">
              <Card>
                <Card-Title :text="session.title" />
                <Card-Image :src="session.image" />
                <Card-Content :text="session.description" />
                <Card-Footer>ID: {{ session.id }}</Card-Footer>
              </Card>
            </Anchor>
          </div>
        </div>
      </PageSection>
    </PageBody>
  </PageWrapper>
</template>
  
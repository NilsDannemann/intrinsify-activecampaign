<script lang="ts" setup>
  // helpers
  import { capitalize } from '~/utils/str'

  // composables
  const { t } = useLang()

  // router
  const route = useRoute()

  // data
  const { data: session } = await useFetch('http://localhost:3004/sessions/' + route.params.session, { initialCache: false })
  // const session = ref({})
  // onMounted(async () => {
  //     session.value = await fetch('http://localhost:3004/sessions/' + route.params.session).then(response => response.json()).catch(error => console.error(error))
  // })

  // layout
  definePageMeta({
    layout: 'page',
  })
  useHead(() => ({
    title: capitalize(route.params.level) + ' ' + capitalize(route.params.session),
    meta: [
      {
        name: 'description',
        content: route.params.session + ' Level',
      },
    ],
  }))
</script>

<template>
  <PageWrapper>
    {{session}}
    <PageHeader>
      <PageTitle :text="session.title" />
    </PageHeader>
    <PageBody>
      <PageSection>
        <p>Route params: {{ route.params }}</p>
        <hr class="my-5">
        <p>Description: {{ session.description }}</p>
      </PageSection>
    </PageBody>
  </PageWrapper>
</template>

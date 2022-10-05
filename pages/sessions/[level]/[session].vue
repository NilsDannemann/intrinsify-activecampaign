<script lang="ts" setup>
  // helpers
  import { capitalize } from '~/utils/str'

  // router
  const route = useRoute()

  // data
  const { data: session } = await useFetch('http://localhost:3004/sessions/' + route.params.session)

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
  // const session = ref({})

  // onMounted(async () => {
  //     session.value = await fetch('http://localhost:3004/sessions/' + route.params.session).then(response => response.json()).catch(error => console.error(error))
  // })
</script>

<template>
  <PageWrapper>
    <PageBody>
      <PageSection>
        <p>Route params: {{ route.params }}</p>
        <p class="font-extrabold">Session title: {{ session.title }}</p>
        <p>Description: {{ session.description }}</p>
      </PageSection>
    </PageBody>
  </PageWrapper>
</template>

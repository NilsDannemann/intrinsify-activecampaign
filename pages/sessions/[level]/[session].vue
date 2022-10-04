<script lang="ts" setup>
definePageMeta({
  layout: 'page',
})
const route = useRoute()
const { data: session } = await useFetch('http://localhost:3004/sessions/' + route.params.session)

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
        <p>Route session: {{ route.params.session }}</p>
        <p class="font-extrabold">Session title: {{ session.title }}</p>
        <p>Description: {{ session.description }}</p>
      </PageSection>
    </PageBody>
  </PageWrapper>
</template>

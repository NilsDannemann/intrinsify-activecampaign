<script lang="ts" setup>
definePageMeta({
  layout: 'page',
})
</script>

<template>
  <PageWrapper class="flex flex-col">
    <ContentDoc>
      <template #default="{ doc }">
        <PageHeader>
          <PageTitle :text="doc.date + ' - ' + doc.title" />
        </PageHeader>
        <PageBody>
          <PageSection>
            <ContentRenderer :value="doc" />
          </PageSection>
        </PageBody>
      </template>
      <template #empty>
        <h1>News is empty</h1>
      </template>
      <template #not-found>
        <Error :code="404" wrap />
      </template>
    </ContentDoc>
  </PageWrapper>
</template>

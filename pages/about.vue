<script lang="ts" setup>
import { capitalize } from '~/utils/str'


const sessionCategories = [
  {
    name: 'Super Session',
    dateCreated: new Date(),
    description: 'Lorem ipsum blah blah lbah'
  },
  {
    name: 'Super Session',
    dateCreated: new Date(),
    description: 'Lorem ipsum blah blah lbah'
  },
]



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
      <PageTitle :text="$t('pages.about.title')" class="capitalize" />
    </PageHeader>
    <PageBody>
      <PageSection>

        <div class="grid lg:grid-cols-4 md:grid-cols-3 sm:grid-cols-1 gap-6">
          <div v-for="i in 4" :key="i">
            <Card>
              <Card-Title>Beginner Sessions</Card-Title>
              <Card-Image><img src="~/assets/images/placeholder-1440x650.jpg"></Card-Image>
              <Card-Content>Lorem ipsum dolor sit amet. Lorem ipsum dolor sit amet, sadipscing elitr, sed eirmod amet.</Card-Content>
              <Card-Footer>Footer Options</Card-Footer>
            </Card>
          </div>
        </div>

      </PageSection>
    </PageBody>
  </PageWrapper>
</template>

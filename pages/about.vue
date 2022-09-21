<script lang="ts" setup>
import { capitalize } from '~/utils/str'

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

        <div class="grid grid-cols-3 gap-3">
          <div v-for="i in 6" :key="i">
            <Card>
              <Card-Title>Beginner Sessions</Card-Title>
              <Card-Content>
                <img src="~/assets/images/placeholder-1440x650.jpg">
                Lorem ipsum dolor sit amet. Lorem ipsum dolor sit amet, sadipscing elitr, sed eirmod amet.
              </Card-Content>
              <Card-Footer>Footer Options</Card-Footer>
            </Card>
          </div>
        </div>

      </PageSection>
    </PageBody>
  </PageWrapper>
</template>

<script lang="ts" setup>
import { capitalize } from '~/utils/str'

// composable
const { t } = useLang()

// compiler macro
definePageMeta({
  layout: 'page',
})
useHead(() => ({
  title: capitalize(t('pages.components.title')),
  meta: [
    {
      name: 'description',
      content: t('pages.components.description'),
    },
  ],
}))
</script>

<template>
  <PageWrapper>
    <PageHeader>
      <PageTitle :text="$t('pages.components.title')" class="capitalize" />
    </PageHeader>
    <PageBody>
      <PageSection>
        
        <h2 class="text-xl font-semibold pb-4">Cards</h2>
        <div class="grid lg:grid-cols-4 md:grid-cols-3 sm:grid-cols-1 gap-6 pb-6">
          <div v-for="i in 4" :key="i">
            <Card>
              <Card-Title>Beginner Sessions</Card-Title>
              <Card-Image><img src="~/assets/images/placeholder-1440x650.jpg"></Card-Image>
              <Card-Content>Lorem ipsum dolor sit amet. Lorem ipsum dolor sit amet, sadipscing elitr, sed eirmod amet.</Card-Content>
              <Card-Footer>Footer Options</Card-Footer>
            </Card>
          </div>
        </div>

        <h2 class="text-xl font-semibold pb-4">Alert</h2>
        <Alert
          type="success"
          title="This is a sample Settings page"
          text="Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua."
          class="mb-6"
        />

        <h2 class="text-xl font-semibold pb-4">Buttons</h2>
        <div class="grid lg:grid-cols-5 md:grid-cols-3 sm:grid-cols-1 gap-6 pb-6">
          <Button type="primary" size="md" text="Button Primary" />
          <Button type="secondary" size="md" text="Button Secondary" />
          <Button type="opposite" size="md" text="Button Opposite" />
          <Button type="secondary" size="sm" text="Button sm" />
          <Button type="secondary" size="xs" text="Button xs" />
        </div>

        <h2 class="text-xl font-semibold pb-4">Tabs</h2>
        <Tabs class="pb-6">
          <Tab name="git" title="git">
            <div class="p-4">
              <p>test 1</p>
            </div>
          </Tab>
          <Tab name="npx" title="npx">
            <div class="p-4">
              <p>test 2</p>
            </div>
          </Tab>
        </Tabs>

        <h2 class="text-xl font-semibold pb-4">Other</h2>
        <Anchor text="headlessui.com" href="https://headlessui.com/vue" />

      </PageSection>
    </PageBody>
  </PageWrapper>
</template>

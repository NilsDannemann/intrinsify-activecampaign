<script lang="ts" setup>
import { capitalize } from '~/utils/str'

// composable
const { t } = useLang()

// compiler macro
definePageMeta({
  layout: 'page',
})
useHead(() => ({
  title: capitalize(t('pages.news.title')),
  meta: [
    {
      name: 'description',
      content: t('pages.news.description'),
    },
  ],
}))
</script>

<template>
  <PageWrapper>
    <PageHeader>
      <PageTitle :text="$t('pages.news.title')" />
    </PageHeader>
    <PageBody>
      <ContentList v-slot="{ list }">
        <PageSection v-for="article in list" :key="article._path">
          <div
            class="block hover:no-underline p-6 flex space-x-6 rounded border border-gray-900/10 dark:border-gray-50/[0.2]"
          >
            <div class="w-30">
              <div class="text-md font-semibold text-slate-800 dark:text-gray-50 mb-1">{{ article.date }}</div>
              <div class="flex items-center space-x-2">
                <img
                  class="w-6 h-6 rounded-full"
                  :src="'/assets/images/avatar-' + article.author + '.jpeg'"
                  :alt="article.author"
                />
                <span class="text-slate-700">{{ article.author }}</span>
              </div>
            </div>
            <div class="flex flex-col">
              <Anchor
                  class="text-xl font-semibold text-slate-800 dark:text-gray-50"
                  :to="article._path"
                >
                {{ article.title }}
              </Anchor>
              <div class="text-slate-700 dark:text-gray-300">
                {{ article.description }}
              </div>
            </div>
          </div>
        </PageSection>
      </ContentList>
    </PageBody>
  </PageWrapper>
</template>

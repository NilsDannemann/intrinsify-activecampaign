<template>
  <BuilderNavbar>
    <template #menu>
      <div class="relative hidden lg:flex items-center ml-auto">
        <div class="flex space-x-4 border-l ml-6 pl-6 border-gray-900/10 dark:border-gray-50/[0.2]">
          <LanguageSwitcher />
          <ThemeSwitcher />
          <Anchor to="/auth" class="hover:no-underline hover:text-slate-900 hover:dark:text-white text-lg flex self-center items-center">
            <IconIc:round-logout />
          </Anchor>
        </div>
      </div>
    </template>
    <template #options="{ toggleOptions }">
      <ActionSheet @onClose="toggleOptions(false)">
        <ActionSheetBody>
          <!-- <ActionSheetHeader text="Menu" /> -->
          <div class="text-sm font-medium capitalize">
            {{ $t('components.theme_switcher.change_theme') }}
          </div>
          <div class="mt-2">
            <ThemeSwitcher type="select-box" />
          </div>
          <div class="mt-6 text-sm font-medium capitalize">
            {{ $t('components.language_switcher.change_language') }}
          </div>
          <div class="mt-2">
            <LanguageSwitcher type="select-box" />
          </div>
        </ActionSheetBody>
        <Button type="secondary" to="/auth" size="sm" class="border-white hover:border-gray-200">
          <IconIc:round-logout />
          <span class="ml-1">Logout</span>
        </Button>
        <Button
          text="Close"
          type="secondary"
          size="sm"
          class="border-white hover:border-gray-200"
          @click.prevent="toggleOptions(false)"
        />
      </ActionSheet>
    </template>
    <template #drawer>
      <slot name="drawer" />
    </template>
  </BuilderNavbar>
</template>

<script lang="ts" setup>
defineProps({
  text: {
    type: String,
    default: '',
  },
  type: {
    type: String,
    default: 'icon',
  },
  to: {
    type: [String, Object],
    default: undefined,
  },
  href: {
    type: String,
    default: undefined,
  },
})

// state:styles
const defaultStyleIcon = `flex items-center mr-4 px-2 py-2 rounded-sm dark:group-hover:highlight-white/10 dark:highlight-white/10 text-slate-500 dark:text-gray-100 group-hover:bg-gray-200 bg-gray-100 dark:group-hover:bg-slate-600 dark:bg-slate-700`

// methods
const onClick = (event: MouseEvent) => {
  const router = useRouter()
  if (props.to) {
    router.push(props.to)
  }
  if (!props.href) {
    event.preventDefault()
  }
}
</script>

<template>
  <NuxtLink v-if="to" class="group flex items-center mb-4 hover:no-underline" tag="a" :to="to" >
    <div :class="`${defaultStyleIcon}`">
      <IconUil:apps class="text-xs" />
    </div>
    <span class="text-sm font-semibold capitalize">
      <slot>{{ text }}</slot>
    </span>
  </NuxtLink>
  <a v-else class="group flex items-center mb-4 hover:no-underline" :href="href" @click="onClick" >
    <div :class="`${defaultStyleIcon}`">
      <IconUil:apps class="text-xs" />
    </div>
    <span class="text-sm font-semibold capitalize">
      <slot>{{ text }}</slot>
    </span>
  </a>
</template>

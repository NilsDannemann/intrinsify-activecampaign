<script lang="ts">
export default defineComponent({
  props: {
    mode: {
      type: String,
      default: 'normal',
    },
  },
  setup() {
    const sidebar = ref(null)

    onMounted(() => {
      // const { onScroll } = useSticky(sidebar.value, -1000)
      // setTimeout(() => onScroll(), 50)
    })

    return {
      sidebar,
    }
  },
})
</script>

<template>
  <div
    ref="sidebar"
    :class="{
      'fixed top-0 hidden pt-20 lg:flex lg:w-60 xl:w-80 h-screen': mode === 'normal',
      'relative flex-1 flex flex-col w-full': mode === 'mobile',
    }"
  >
    <div class="flex-1 overflow-y-auto pl-4 lg:pl-0 pr-4 py-4">
      <ul>
        <li>
          <DashboardSidebarItem text="Home" to="/dashboard"/>
        </li>
        <li>
          <DashboardSidebarItem text="Content Sample 1" to="/dashboard/content-sample-1"/>
        </li>
        <li>
          <DashboardSidebarItem text="Content Sample 2" to="/dashboard/content-sample-2"/>
        </li>
        <li>
          <DashboardSidebarItem text="Content Sample 3" to="/dashboard/content-sample-3"/>
        </li>
        <li v-for="i in 29" :key="i">
          <DashboardSidebarItem text="Content Sample 3" to="/dashboard/content-sample-3"/>
        </li>
      </ul>
    </div>
  </div>
</template>

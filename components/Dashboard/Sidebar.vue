<template>
  <div ref="sidebar" :class="{ 'fixed top-0 hidden pt-16 lg:flex lg:w-60 xl:w-80 h-screen': mode === 'normal', 'relative flex-1 flex flex-col w-full': mode === 'mobile' }">
    <div class="flex-1 overflow-y-auto pl-4 lg:pl-0 pr-4 py-4">
      <ul>
        <li v-for="i in 29" :key="i">
          <a href="/docs/installation" class="group flex items-center mb-4">
            <div
              class="mr-4 p-1.5 rounded-md ring-1 ring-slate-900/5 shadow-sm group-hover:shadow group-hover:ring-slate-900/10 dark:ring-0 dark:shadow-none dark:group-hover:shadow-none dark:group-hover:highlight-white/10 group-hover:shadow-sky-200 dark:highlight-white/10"
              :class="{
                'dark:group-hover:bg-sky-500 dark:bg-sky-500': (i === 1),
                'dark:group-hover:bg-slate-700 dark:bg-slate-700': (i !== 1),
              }"
            >
              <IconUil:apps class="text-white text-xs" />
            </div>
            <span class="text-sm font-semibold" :class="{ 'font-extrabold text-sky-500 dark:text-sky-400': (i === 1) }">Dashboard</span>
          </a>
        </li>
      </ul>
      awewae
    </div>
  </div>
</template>

<script lang="ts">

export default defineComponent({
  props: {
    mode: {
      type: String,
      default: 'normal'
    }
  },
  setup() {
    const sidebar = ref(null)
    
    onMounted(() => {
      // const { onScroll } = useSticky(sidebar.value, -1000)
      // setTimeout(() => onScroll(), 50)
    })

    return {
      sidebar
    }
  }
})
</script>
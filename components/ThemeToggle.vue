<template>
  <div class="flex items-center">
    <Listbox v-if="currentStyle === 'dropdown-right-top'" v-model="themeSetting">
      <ListboxLabel class="sr-only">Theme</ListboxLabel>
      <ListboxButton type="button">
        <span class="flex justify-center items-center dark:hidden">
          <IconUil:sun />
        </span>
        <span class="justify-center items-center hidden dark:flex">
          <IconUil:moon />
        </span>
      </ListboxButton>
      <ListboxOptions class="p-1 absolute z-50 top-full right-0 outline-none bg-white rounded-lg ring-1 ring-gray-900/10 shadow-lg overflow-hidden w-36 py-1 text-sm text-gray-700 font-semibold dark:bg-gray-800 dark:ring-0 dark:highlight-white/5 dark:text-gray-300">
        <ListboxOption 
          v-for="theme in [
            { key: 'light', text: 'Light' },
            { key: 'dark', text: 'Dark' },
            { key: 'system', text: 'System' },
            { key: 'realtime', text: 'Realtime' },
          ]"
          :key="theme.key"
          :value="theme.key"
          :class="{ 
            'py-2 px-2 flex items-center cursor-pointer': true,
            'text-sky-500 bg-gray-50 dark:bg-gray-600/30': (themeSetting === theme.key),
          }"
        >
          <span class="text-sm mr-2">
            <IconUil:sun v-if="theme.key === 'light'" />
            <IconUil:moon v-else-if="theme.key === 'dark'" />
            <IconUil:laptop v-else-if="theme.key === 'system'" />
            <IconUil:clock v-else-if="theme.key === 'realtime'" />
          </span>
          {{ theme.text }}
        </ListboxOption>
      </ListboxOptions>
    </Listbox>
    <select v-if="currentStyle === 'select-box'" v-model="themeSetting" class="w-full px-2 pr-3 py-1 outline-none rounded border bg-transparent text-gray-700 dark:text-gray-300 border-gray-900/10 dark:border-gray-50/[0.2]">
      <option value="light">Light</option>{
    type: {
      type: String,
      default: 'dropdown-right-top',
    },
  }
      <option value="dark">Dark</option>
      <option value="system">System</option>
      <option value="realtime">Realtime</option>
    </select>
  </div>
</template>

<script lang="ts" setup>
import {
  Listbox,
  ListboxButton,
  ListboxLabel,
  ListboxOptions,
  ListboxOption,
} from '@headlessui/vue'
import { IThemeSettingOptions, ITheme } from '~/utils/theme'

// micro compiler
const props = defineProps({
  type: {
    type: String,
    default: 'dropdown-right-top',
  },
})

// state
const themeSetting = useState<IThemeSettingOptions>('theme.setting')
const currentStyle = toRef(props, 'type')
</script>
<script lang="ts" setup>
import { IApp } from '~/utils/app'

export interface IMenuItem {
  type: 'link' | 'button'
  text: string
  href?: any
  route?: any
}

const { t } = useLang()
const app = useState<IApp>('app')
const menus = computed((): IMenuItem[] => [
  { type: 'link', text: 'work', route: { name: 'post' } },
  { type: 'link', text: 'about', route: { name: 'about' } },
  // { type: 'link', text: 'resumé', route: { name: 'settings' } },
  // { type: 'link', text: t('pages.blank.nav'), route: { name: 'blank' } },
  // { type: 'link', text: t('pages.test.nav'), route: { name: 'test' } },
  // { type: 'link', text: t('pages.setting.nav'), route: { name: 'setting' } },
])
</script>

<template>
  <div
    class="
      relative
      flex
      justify-center
      pt-6
      pb-2
    "
  >
    <nav
      class="text leading-6 text-gray-600 dark:text-gray-300"
      role="navigation"
    >
      <ul class="flex gap-4 rounded-full px-3 shadow-zinc-800/5 ring-1 ring-zinc-900/5 backdrop-blur  dark:text-zinc-200 dark:ring-white/10 transition">
        <li v-for="(item, i) in menus" :key="i">
          <Anchor
            v-if="item.type === 'link'"
            :to="item.route ? item.route : undefined"
            :href="item.href ? item.href : undefined"
            class="
              hover:no-underline hover:text-slate-900 hover:dark:text-white
              capitalize
              flex
              px-3 py-2
              transition
            "
          >
          {{ item.text }}
          </Anchor>
        </li>
      </ul>
    </nav>
  </div>
</template>
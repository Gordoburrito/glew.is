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
  { type: 'link', text: 'work', route: { name: 'post' }, logo: true },
  { type: 'link', text: 'about', route: { name: 'about' } },
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
      border border-gray-900/10
      dark:border-gray-50/[0.2]
      p-2
    "
  >
    <nav
      class="text leading-6 text-gray-600 dark:text-gray-300"
      role="navigation"
    >
      <ul class="flex items-center space-x-8">
        <li v-for="(item, i) in menus" :key="i">
          <Anchor
            v-if="item.type === 'link'"
            :to="item.route ? item.route : undefined"
            :href="item.href ? item.href : undefined"
            class="
              hover:no-underline hover:text-slate-900 hover:dark:text-white
              capitalize
              flex
              gap-2
            "
          >
            <div
              v-if="item.logo"
              class="
                hover:no-underline hover:text-slate-900 hover:dark:text-white
                flex
                self-center
                items-center
              "
            >
              <IconMdi:github-face />
            </div>
            {{ item.text }}
          </Anchor>
        </li>
      </ul>
    </nav>
  </div>
</template>
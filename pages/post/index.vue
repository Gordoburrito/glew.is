<script lang="ts" setup>
import { capitalize } from '~/utils/str'

// composable
const { t } = useLang()

// compiler macro
definePageMeta({
  layout: 'page',
})
useHead(() => ({
  title: capitalize(t('pages.post.title')),
  meta: [
    {
      name: 'description',
      content: t('pages.post.description'),
    },
  ],
}))
</script>

<template>
  <PageWrapper>
    <PageBody>
      <PageSection class="flex-col flex items-center lg:mb-16 md:mb-14 sm:mb-8">
        <h2 class="text-4xl font-bold">Gordon Lewis</h2>
        <h3 class="text-2xl">Creative Developer</h3>
        <p class="text-xl text-center pt-8">
          Working towards a more humane represantation of thought.
        </p>
        <Socials/>
      </PageSection>
      <ContentList v-slot="{ list }">
        <div class="lg:columns-3 md:columns-2 lg:px-8 px-4 gap-1.5rem">
          <PageSection
            v-for="article in list"
            :key="article._path"
            class="md:flex-1 lg:px-0 px-0"
          >
            <NuxtLink
              :to="article._path"
              class="flex self-center items-center text-slate-50 hover:no-underline hover:text-white group"
            >
              <Card
                :class="`bg-blue-700 group-hover:to-blue-700 flex ${article.class}`"
              >
                <CardContent>
                  <p class="mb-6 uppercase tracking-widest">
                    {{ article.subtitle }}
                  </p>
                  <CardTitle
                    class="lg:text-4xl text-3xl mb-4"
                    :text="article.title"
                  />
                  <p class="text-xl mb-10">{{ article.description }}</p>
                  <div
                    class="group-hover:ml-6 ease-in-out duration-300 delay-100"
                  >
                    <IconMdi:arrow-forward class="text-4xl" />
                  </div>
                </CardContent>
              </Card>
            </NuxtLink>
          </PageSection>
        </div>
      </ContentList>
    </PageBody>
  </PageWrapper>
</template>

<style lang="scss" scoped>
@media only screen and (min-width: 768px) {
  .tall {
    height: 420px;
  }
}
@media only screen and (min-width: 1024px) {
  .tall {
    height: 600px;
  }
}
</style>

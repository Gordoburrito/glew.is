<script lang="ts" setup>
import { capitalize } from '~/utils/str'

// composable
const { t } = useLang()

// compiler macro
definePageMeta({
  layout: 'page',
})
useHead(() => ({
  title: capitalize(t('pages.about.title')),
  meta: [
    {
      name: 'description',
      content: t('pages.about.description'),
    },
  ],
}))
</script>

<template>
  <PageWrapper>
    <PageHeader>
      <PageTitle text="About" class="capitalize" />
    </PageHeader>
    <PageBody>
      <PageSection>
        <p>
          I love to craft delightful tools using development to enhance experiences for people in my community. I’m looking for more opportunities to more effectively identify problems and effectively deliver solutions.
        </p>
        <p>I love to think about all the things I could make.</p>
        <p>I draw too</p>
        Here's a pic of me
        Here's my resumé
        Here's some art and illustration.
        If you don't like it turn to page 3, if you do like it there is no page 3 that was just to get rid of the haters.
      </PageSection>
    </PageBody>
  </PageWrapper>
</template>

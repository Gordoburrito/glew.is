<script lang="ts" setup>
// composable
const { t } = useLang()

// meta
definePageMeta({
  layout: 'page',
})

// vars
const titlesText = computed<string[]>(() => t('pages.index.title').split('[]'))
const leadingsText = computed(() => [
  {
    text: titlesText.value[0],
    startColor: '#007CF0',
    endColor: '#00DFD8',
    delay: 0,
  },
  {
    text: titlesText.value[1],
    startColor: '#7928CA',
    endColor: '#FF0080',
    delay: 2,
  },
  {
    text: titlesText.value[2],
    startColor: '#FF4D4D',
    endColor: '#F9CB28',
    delay: 4,
  },
])
const tooltip = ref(false)

// const
const cancelTooltip = () => {
  tooltip.value = false
  const tt = document.querySelector('.tooltiptext')
  if (tt) tt.innerHTML = `Copy to clipboard`
}
const copyBash = () => {
  const bash = 'git clone https://github.com/viandwi24/nuxt3-awesome-starter'
  navigator.clipboard.writeText(bash)
  tooltip.value = true
  const tt = document.querySelector('.tooltiptext')
  if (tt) tt.innerHTML = `Copied!!!`
}
</script>

<template></template>

<style lang="scss">
@import '../assets/sass/variables';
</style>

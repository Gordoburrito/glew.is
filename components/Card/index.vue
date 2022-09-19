<script lang="ts" setup>
defineProps({
  disabled: {
    type: Boolean,
    required: false,
  },
})
</script>

<template>
  <div
    class="card duration-300 transition-colors w-full relative rounded-3xl overflow-hidden"
  >
    <div
      v-if="disabled"
      class="absolute z-10 top-0 left-0 w-full h-full bg-slate-800/[0.75] cursor-not-allowed"
    />
    <slot />
  </div>
</template>

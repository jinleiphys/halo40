<script setup lang="ts">
import { computed } from 'vue'

interface Props {
  background?: string
  authors?: string[]
  meeting?: string
  preTitle?: string
  preDate?: boolean
}

const props = withDefaults(defineProps<Props>(), {
  background: undefined,
  authors: () => [],
  meeting: '',
  preTitle: '',
  preDate: true
})

// Process authors into names and institutes
const processedAuthors = computed(() => {
  return props.authors.map((author, index) => {
    const parts = author.split('^')
    return {
      name: parts[0],
      institute: parts[1] || '',
      index: index
    }
  })
})

// Generate current date
const currentDate = computed(() => {
  return new Date().toLocaleDateString('en-US', {
    year: 'numeric',
    month: 'long',
    day: 'numeric'
  })
})

// Dynamic background style
const backgroundStyle = computed(() => {
  return props.background ? { backgroundImage: `url(${props.background})` } : {}
})
</script>

<template>
  <div class="slidev-layout cover" :style="backgroundStyle">
    <div class="my-auto w-full text-center">
      <div v-if="preTitle" class="text-lg opacity-70 mb-2">{{ preTitle }}</div>
      
      <slot name="title">
        <h1 class="gradient-text">{{ $slidev.configs.title }}</h1>
      </slot>
      
      <div v-if="meeting" class="meeting">{{ meeting }}</div>
      
      <div v-if="authors.length > 0" class="authors">
        <span v-for="(author, index) in processedAuthors" :key="index">
          <span :class="{ 'underline-text': index === 0 }">{{ author.name }}</span>
          <sup v-if="author.institute">{{ author.institute }}</sup>
          <span v-if="index < processedAuthors.length - 2">, </span>
          <span v-else-if="index === processedAuthors.length - 2"> and </span>
        </span>
      </div>
      
      <div v-if="preDate" class="date">{{ currentDate }}</div>
      
      <slot />
    </div>
  </div>
</template>

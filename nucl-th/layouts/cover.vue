<script setup lang="ts">
import { computed } from 'vue'

interface Props {
  background?: string
  authors?: string[] | Record<string, string[]>[]
  meeting?: string
  preTitle?: string
  preDate?: boolean
  date?: string
}

const props = withDefaults(defineProps<Props>(), {
  background: undefined,
  authors: () => [],
  meeting: '',
  preTitle: '',
  preDate: true,
  date: undefined
})

// Process authors into names and institutes
const processedAuthors = computed(() => {
  if (!props.authors || props.authors.length === 0) {
    return []
  }

  // Check if it's the new object format
  if (typeof props.authors[0] === 'object' && !Array.isArray(props.authors[0])) {
    const authorObjects = props.authors as Record<string, string[]>[]
    return authorObjects.map((authorObj, index) => {
      const name = Object.keys(authorObj)[0]
      const affiliations = authorObj[name]
      return {
        name: name,
        institute: affiliations.length > 0 ? (index + 1).toString() : '',
        affiliations: affiliations,
        index: index
      }
    })
  }

  // Legacy string format with ^ notation
  const authorStrings = props.authors as string[]
  return authorStrings.map((author, index) => {
    const parts = author.split('^')
    return {
      name: parts[0],
      institute: parts[1] || '',
      affiliations: [],
      index: index
    }
  })
})

// Generate affiliations list for the new format
const affiliationsList = computed(() => {
  if (!props.authors || props.authors.length === 0) {
    return []
  }

  // Only generate for new object format
  if (typeof props.authors[0] === 'object' && !Array.isArray(props.authors[0])) {
    const authorObjects = props.authors as Record<string, string[]>[]
    return authorObjects.map((authorObj, index) => {
      const affiliations = Object.values(authorObj)[0]
      return {
        number: index + 1,
        affiliations: affiliations
      }
    }).filter(item => item.affiliations.length > 0)
  }

  return []
})

// Generate current date or use provided date
const currentDate = computed(() => {
  if (props.date) {
    return props.date
  }
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
      
      <div v-if="affiliationsList.length > 0" class="affiliations">
        <div v-for="affiliation in affiliationsList" :key="affiliation.number" class="affiliation-item">
          <sup>{{ affiliation.number }}</sup>
          <span v-for="(aff, index) in affiliation.affiliations" :key="index">
            {{ aff }}<span v-if="index < affiliation.affiliations.length - 1">, </span>
          </span>
        </div>
      </div>
      
      <div v-if="preDate" class="date">{{ currentDate }}</div>
      
      <slot />
    </div>
    
    <!-- Logo in bottom right corner -->
    <div class="logo-container">
      <img src="/logo.png" alt="Logo" class="logo" />
    </div>
  </div>
</template>

<style scoped>
.logo-container {
  position: absolute;
  bottom: 1.5rem;
  right: 1.5rem;
  z-index: 10;
}

.logo {
  height: 8rem;
  width: auto;
  opacity: 0.8;
  transition: opacity 0.3s ease;
}

.logo:hover {
  opacity: 1;
}
</style>

<script setup lang="ts">
import { computed } from 'vue'
import BarBottom from '../components/BarBottom.vue'

// Get configuration from frontmatter
const title = $slidev.configs.title || ''
const meeting = $slidev.configs.meeting || ''
const meetingShort = $slidev.configs.meetingShort || ''

// Extract first author from authors array or fall back to author field
const author = computed(() => {
  if ($slidev.configs.authors && Array.isArray($slidev.configs.authors) && $slidev.configs.authors.length > 0) {
    const firstAuthor = $slidev.configs.authors[0]
    
    // Check if it's the new object format
    if (typeof firstAuthor === 'object' && !Array.isArray(firstAuthor)) {
      // Get the first key (author name) from the object
      const authorName = Object.keys(firstAuthor)[0]
      return authorName || ''
    }
    
    // Legacy string format with ^ notation
    if (typeof firstAuthor === 'string') {
      return firstAuthor.split('^')[0].trim()
    }
  }
  return $slidev.configs.author || ''
})
</script>

<template>
  <div class="slidev-layout default">
    <div class="content-area">
      <slot />
    </div>
    
    <BarBottom 
      :title="title"
      :author="author" 
      :meeting="meeting"
      :meetingShort="meetingShort"
    />
  </div>
</template>

<style scoped>
.content-area {
  padding-bottom: 2.5rem; /* Reduced space for smaller footer */
  height: calc(100vh - 2.5rem);
  overflow-y: auto;
}
</style>
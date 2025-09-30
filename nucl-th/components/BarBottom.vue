<script setup lang="ts">
import { computed } from 'vue'

interface Props {
  title?: string
  author?: string
  meeting?: string
  meetingShort?: string
}

const props = withDefaults(defineProps<Props>(), {
  title: '',
  author: '',
  meeting: '',
  meetingShort: ''
})

// Get slide info from Slidev globals
const slideInfo = computed(() => {
  if (typeof $slidev !== 'undefined') {
    return {
      current: $slidev.nav.currentPage,
      total: $slidev.nav.total
    }
  }
  return { current: 1, total: 1 }
})
</script>

<template>
  <div class="bar-bottom">
    <div class="bar-left">
      <span v-if="author" class="author">{{ author }}</span>
      <span v-if="author && title" class="divider">|</span>
      <span v-if="title" class="title">{{ title }}</span>
    </div>
    
    <div class="bar-center">
      <span v-if="meetingShort || meeting" class="meeting">{{ meetingShort || meeting }}</span>
    </div>
    
    <div class="bar-right">
      <slot />
    </div>
    
    <div class="bar-pagination">
      <span class="slide-number">{{ slideInfo.current }} / {{ slideInfo.total }}</span>
    </div>
  </div>
</template>

<style scoped>
.bar-bottom {
  position: fixed;
  bottom: 0;
  left: 0;
  right: 0;
  height: 1.75rem;
  background: linear-gradient(90deg, var(--slidev-theme-primary) 0%, var(--slidev-theme-secondary) 50%, var(--slidev-theme-accent) 100%);
  background-size: 200% 100%;
  animation: gradient-shift 6s ease infinite;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 0 1.5rem;
  color: white;
  font-family: var(--slidev-font-sans);
  font-size: 0.65rem;
  font-weight: 500;
  z-index: 100;
  box-shadow: 0 -2px 8px rgba(0, 0, 0, 0.1);
}

@keyframes gradient-shift {
  0%, 100% {
    background-position: 0% 50%;
  }
  50% {
    background-position: 100% 50%;
  }
}

.bar-left {
  display: flex;
  align-items: center;
  gap: 0.75rem;
  flex: 1;
}

.bar-center {
  display: flex;
  align-items: center;
  justify-content: center;
  flex: 2;
  text-align: center;
  overflow: hidden;
}

.bar-right {
  display: flex;
  align-items: center;
  justify-content: flex-end;
  flex: 1;
}

.bar-pagination {
  display: flex;
  align-items: center;
  margin-left: 1rem;
}

.author, .title, .meeting, .slide-number {
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}

.divider {
  opacity: 0.7;
  margin: 0 0.5rem;
}

.meeting {
  font-style: italic;
  opacity: 0.9;
  color: #FFD700; /* Gold color to stand out */
  max-width: 100%;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}

.slide-number {
  font-weight: 600;
  background: rgba(255, 255, 255, 0.2);
  padding: 0.125rem 0.5rem;
  border-radius: 0.75rem;
  backdrop-filter: blur(4px);
  font-size: 0.7rem;
}
</style>
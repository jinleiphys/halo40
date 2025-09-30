<script setup lang="ts">
import { computed } from 'vue'

interface Props {
  type?: 'info' | 'warning' | 'default'
  x?: string | number
  y?: string | number
  width?: string | number
  height?: string | number
  fontSize?: string | number
}

const props = withDefaults(defineProps<Props>(), {
  type: 'default',
  x: 'auto',
  y: 'auto',
  width: 'auto',
  height: 'auto',
  fontSize: '1rem'
})

const boxStyle = computed(() => {
  const style: Record<string, string> = {}
  
  if (props.x !== 'auto') {
    style.left = typeof props.x === 'number' ? `${props.x}px` : props.x
    style.position = 'absolute'
  }
  
  if (props.y !== 'auto') {
    style.top = typeof props.y === 'number' ? `${props.y}px` : props.y
    style.position = 'absolute'
  }
  
  if (props.width !== 'auto') {
    style.width = typeof props.width === 'number' ? `${props.width}px` : props.width
  }
  
  if (props.height !== 'auto') {
    style.height = typeof props.height === 'number' ? `${props.height}px` : props.height
  }
  
  style.fontSize = typeof props.fontSize === 'number' ? `${props.fontSize}px` : props.fontSize
  
  return style
})

const boxClass = computed(() => {
  const classes = ['text-box']
  classes.push(`text-box--${props.type}`)
  return classes.join(' ')
})
</script>

<template>
  <div :class="boxClass" :style="boxStyle">
    <slot />
  </div>
</template>

<style scoped>
.text-box {
  padding: 1.5rem; /* Reasonable padding */
  border-radius: 0.75rem;
  border: 2px solid; /* Keep thicker border for visibility */
  background-color: rgba(255, 255, 255, 0.95);
  box-shadow: 0 4px 16px rgba(0, 0, 0, 0.15);
  font-size: 1.125rem; /* ~18px - matches body text */
  line-height: 1.6;
}

.text-box--default {
  border-color: var(--slidev-theme-primary);
  background-color: rgba(15, 163, 177, 0.05);
}

.text-box--info {
  border-color: var(--slidev-theme-secondary);
  background-color: rgba(78, 197, 212, 0.1);
  color: var(--slidev-theme-accent);
}

.text-box--warning {
  border-color: #f59e0b;
  background-color: rgba(245, 158, 11, 0.1);
  color: #92400e;
}

.text-box p {
  margin: 0;
  font-size: 1.125rem; /* Match the box base size */
}

.text-box p + p {
  margin-top: 0.75rem; /* Reasonable spacing between paragraphs */
}

.text-box h1,
.text-box h2,
.text-box h3,
.text-box h4 {
  font-size: 1.25rem; /* Slightly larger headings in text boxes */
  margin-bottom: 0.75rem;
}

.text-box ul,
.text-box ol {
  font-size: 1.125rem;
}

.text-box li {
  margin-bottom: 0.5rem;
}
</style>
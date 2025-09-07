<script setup>
import AboutMe from './components/AboutMe.vue'
import { ref, onMounted, computed } from 'vue'

const THEME_KEY = 'theme'

function getPreferredTheme() {
  const saved = localStorage.getItem(THEME_KEY)
  if (saved === 'light' || saved === 'dark') return saved
  const prefersDark = window.matchMedia('(prefers-color-scheme: dark)').matches
  return prefersDark ? 'dark' : 'light'
}

function applyTheme(theme) {
  const root = document.documentElement
  if (theme === 'dark') {
    root.setAttribute('data-theme', 'dark')
  } else {
    root.removeAttribute('data-theme')
  }
}

const currentTheme = ref('light')

onMounted(() => {
  currentTheme.value = getPreferredTheme()
  applyTheme(currentTheme.value)
})

function toggleTheme() {
  currentTheme.value = currentTheme.value === 'dark' ? 'light' : 'dark'
  localStorage.setItem(THEME_KEY, currentTheme.value)
  applyTheme(currentTheme.value)
}

const themeLabel = computed(() => (currentTheme.value === 'dark' ? 'Темная' : 'Светлая'))
</script>

<template>
  <button class="theme-toggle" @click="toggleTheme" aria-label="Переключить тему">
    {{ themeLabel }} тема
  </button>
  <AboutMe />
  
</template>

<style scoped>
</style>

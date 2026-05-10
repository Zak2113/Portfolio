<template>
  <nav class="navbar">
    <a href="#" class="logo">Zakaria Abdullahi</a>

    <div class="nav-controls">
      
      <a href="#work-projects" class="nav-link">Work Projects</a>
      <a href="#personal-projects" class="nav-link">Personal Projects</a>
      <a href="#experience" class="nav-link">Experience</a>

      <div class="divider"></div>

      <button @click="toggleTheme" class="theme-toggle" aria-label="Toggle dark mode">
        <svg v-if="!isDarkMode" viewBox="0 0 24 24" width="20" height="20" stroke="currentColor" stroke-width="2" fill="none" stroke-linecap="round" stroke-linejoin="round">
          <circle cx="12" cy="12" r="5"></circle>
          <line x1="12" y1="1" x2="12" y2="3"></line>
          <line x1="12" y1="21" x2="12" y2="23"></line>
          <line x1="4.22" y1="4.22" x2="5.64" y2="5.64"></line>
          <line x1="18.36" y1="18.36" x2="19.78" y2="19.78"></line>
          <line x1="1" y1="12" x2="3" y2="12"></line>
          <line x1="21" y1="12" x2="23" y2="12"></line>
          <line x1="4.22" y1="19.78" x2="5.64" y2="18.36"></line>
          <line x1="18.36" y1="5.64" x2="19.78" y2="4.22"></line>
        </svg>
        
        <svg v-else viewBox="0 0 24 24" width="20" height="20" stroke="currentColor" stroke-width="2" fill="none" stroke-linecap="round" stroke-linejoin="round">
          <path d="M21 12.79A9 9 0 1 1 11.21 3 7 7 0 0 0 21 12.79z"></path>
        </svg>
      </button>

    </div>
  </nav>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const isDarkMode = ref(false)

const toggleTheme = () => {
  isDarkMode.value = !isDarkMode.value
  const theme = isDarkMode.value ? 'dark' : 'light'
  
  if (import.meta.client) { 
    document.documentElement.setAttribute('data-theme', theme)
    localStorage.setItem('theme', theme)
  }
}

onMounted(() => {
  const savedTheme = localStorage.getItem('theme')
  const systemPrefersDark = window.matchMedia && window.matchMedia('(prefers-color-scheme: dark)').matches

  if (savedTheme === 'dark' || (!savedTheme && systemPrefersDark)) {
    isDarkMode.value = true
    document.documentElement.setAttribute('data-theme', 'dark')
  }
})
</script>

<style scoped>
.navbar {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 1rem 5%;
  background-color: var(--card-bg, #ffffff);
  border-bottom: 1px solid var(--border-color, #eaeaea);
  position: sticky;
  top: 0;
  z-index: 100;
}

.logo {
  font-weight: 700;
  font-size: 1.2rem;
  color: var(--text-main, #1e293b);
  text-decoration: none;
}

.nav-controls {
  display: flex;
  align-items: center;
  gap: 1.5rem; 
}

.nav-link {
  text-decoration: none;
  color: var(--text-light, #64748b);
  font-size: 0.95rem;
  font-weight: 500;
  transition: color 0.2s;
}

.nav-link:hover {
  color: var(--primary-color, #3b82f6);
}

.divider {
  width: 1px;
  height: 24px;
  background-color: var(--border-color, #e2e8f0);
  margin: 0 0.5rem;
}

/* Sleek Theme Toggle Button */
.theme-toggle {
  background: transparent;
  border: none;
  color: var(--text-light, #64748b);
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 0.4rem;
  border-radius: 6px;
  transition: all 0.2s ease;
}

.theme-toggle:hover {
  background-color: rgba(100, 116, 139, 0.1); 
  color: var(--text-main, #1e293b);
}

/* Responsive adjustment for mobile */
@media (max-width: 600px) {
  .nav-link {
    display: none; /* Hides text links on small screens */
  }
  .divider {
    display: none;
  }
}
</style>
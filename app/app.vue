<template>
  <div>
    <NavBar />

    <div class="container">
      
      <header class="hero">
        <span class="badge">Computer Science Student</span>
        <h1>Hi, I'm Zakaria.<br>I build things for the web.</h1>
        <p>I'm a student at Concordia University passionate about software development, problem-solving, and creating clean, user-friendly applications.</p>
        
        <div class="btn-group">
          <a href="https://github.com/zak2113" target="_blank" class="btn btn-primary">View GitHub</a>
          <a href="https://linkedin.com/in/zak-abdi" target="_blank" class="btn btn-outline">Connect on LinkedIn</a>
        </div>
      </header>

      <section id="work-projects">
        <h2 class="section-header">Work </h2>
        <div class="grid">
          <ProjectCard 
            v-for="(project, index) in workProjects" 
            :key="index"
            :title="project.title"
            :description="project.description"
            :link="project.link"
            :tags="project.tags"
          />
        </div>
      </section>

      <section id="personal-projects">
        <h2 class="section-header">Personal & Academic Projects</h2>
        <div class="grid">
          <ProjectCard 
            v-for="(project, index) in personalProjects" 
            :key="index"
            :title="project.title"
            :description="project.description"
            :link="project.link"
            :tags="project.tags"
          />
        </div>
      </section>
      <!-- 
      <section id="experience">
        <h2 class="section-header">Work Experience</h2>
        <ExperienceItem 
          v-for="(job, index) in jobs" 
          :key="index"
          :role="job.role"
          :company="job.company"
          :date="job.date"
          :bullets="job.bullets"
        />
      </section>
      -->
    </div>

    <footer>
      <p>&copy; {{ new Date().getFullYear() }} Zakaria. Built with Nuxt.</p>
    </footer>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'

useHead({
  title: 'Your Name - Student Portfolio',
  meta: [{ name: 'description', content: 'Computer Science student portfolio showcasing web development projects.' }]
})

// --- Theme Toggle Logic ---
const isDarkMode = ref(false)

const toggleTheme = () => {
  isDarkMode.value = !isDarkMode.value
  const theme = isDarkMode.value ? 'dark' : 'light'
  
  // Update the HTML attribute
  document.documentElement.setAttribute('data-theme', theme)
  // Save to local storage so it remembers on reload
  localStorage.setItem('theme', theme)
}

onMounted(() => {
  // When page loads, check if they previously chose dark mode OR if their computer is set to dark mode
  const savedTheme = localStorage.getItem('theme')
  const systemPrefersDark = window.matchMedia && window.matchMedia('(prefers-color-scheme: dark)').matches

  if (savedTheme === 'dark' || (!savedTheme && systemPrefersDark)) {
    isDarkMode.value = true
    document.documentElement.setAttribute('data-theme', 'dark')
  }
})




useHead({
  title: 'Zakaria Abdullahi - Student Portfolio',
  meta: [{ name: 'description', content: 'Computer Science student portfolio showcasing web development projects.' }]
})

// Data Arrays for Components
const workProjects = [
  {
    title: 'Terroirs Restaurant',
    description: "A clean, responsive informational website designed to establish the restaurant's digital presence, highlighting its unique dining atmosphere and culinary focus while providing a streamlined contact form for direct customer inquiries.",
    link: 'https://terroirsrestaurant.ca',
    tags: ['Wordpress']
  }
  
]

const personalProjects = [
  {
    title: 'Noodle Learning Management System',
    description: 'An intuitive learning management platform designed to seamlessly connect students and instructors through centralized course organization, real-time grade tracking, and a unified assessment calendar.',
    link: 'https://noodle.zakabdi.dev',
    tags: ['NextJS','NodeJS','SQLite']
  },
  {
    title: 'Investment Calculator',
    description: 'A dynamic financial tool featuring an interactive investment calculator that empowers users to project and visualize their long-term wealth growth through customizable parameters and detailed timeline graphs.',
    link: 'https://investmentcalc.zakabdi.dev',
    tags: ['React', 'NodeJS']
  }
]

const jobs = [
  {
    role: 'Customer Service Representative',
    company: '[Company Name] • [City, State]',
    date: 'May 2022 - Present',
    bullets: [
      'Acted as the primary point of contact for clients, successfully diagnosing and resolving over 40+ customer issues daily.',
      'Collaborated cross-functionally with team members to streamline intake processes, reducing average customer wait times by 15%.',
      'Developed strong active listening and de-escalation skills, maintaining a 98% positive customer satisfaction rating.',
      'Leveraged technical internal software to log data accurately and maintain detailed client records.'
    ]
  }
]
</script>

<style>
/* Global CSS variables and layout styles remain here */
:root {
  --bg-color: #f8fafc;
  --text-main: #1e293b;
  --text-light: #64748b;
  --primary-color: #3b82f6;
  --primary-hover: #2563eb;
  --card-bg: #ffffff;
  --border-color: #e2e8f0;
}

/* Add this Dark Mode block! */
[data-theme="dark"] {
  --bg-color: #0f172a;       /* Dark blue/slate background */
  --text-main: #f8fafc;      /* White text */
  --text-light: #94a3b8;     /* Light gray text */
  --card-bg: #1e293b;        /* Slightly lighter dark background for cards */
  --border-color: #334155;   /* Dark border */
  --primary-color: #60a5fa;  /* Slightly lighter blue for better contrast */
  --primary-hover: #3b82f6;
}

/* Add styles for the toggle button */
.theme-toggle {
  background: var(--bg-color);
  border: 1px solid var(--border-color);
  color: var(--text-main);
  padding: 0.4rem 0.8rem;
  border-radius: 6px;
  cursor: pointer;
  font-weight: 600;
  font-size: 0.9rem;
  transition: all 0.2s ease;
  display: flex;
  align-items: center;
  gap: 0.4rem;
}

.theme-toggle:hover {
  background-color: var(--border-color);
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
}

html { scroll-behavior: smooth; }
body { background-color: var(--bg-color); color: var(--text-main); line-height: 1.6; }

nav {
  background-color: var(--card-bg);
  padding: 1.2rem 5%;
  display: flex;
  justify-content: space-between;
  align-items: center;
  border-bottom: 1px solid var(--border-color);
  position: sticky;
  top: 0;
  z-index: 100;
}
.logo { font-weight: 700; font-size: 1.2rem; color: var(--text-main); text-decoration: none; }
.nav-links { display: flex; gap: 1.5rem; flex-wrap: wrap; }
.nav-links a { text-decoration: none; color: var(--text-light); font-weight: 500; font-size: 0.95rem; transition: color 0.2s; }
.nav-links a:hover { color: var(--primary-color); }

.container { max-width: 900px; margin: 0 auto; padding: 0 2rem; }
section { padding: 4rem 0; border-bottom: 1px solid var(--border-color); }
section:last-of-type { border-bottom: none; }
.section-header { font-size: 1.75rem; font-weight: 700; margin-bottom: 2rem; color: var(--text-main); }

.hero { padding: 6rem 0 4rem; text-align: left; border-bottom: 1px solid var(--border-color); }
.badge { display: inline-block; background-color: #dbeafe; color: #1e40af; padding: 0.3rem 0.8rem; border-radius: 20px; font-size: 0.85rem; font-weight: 600; margin-bottom: 1.5rem; }
.hero h1 { font-size: 3rem; font-weight: 800; line-height: 1.2; margin-bottom: 1rem; color: var(--text-main); }
.hero p { font-size: 1.15rem; color: var(--text-light); max-width: 600px; margin-bottom: 2rem; }

.btn-group { display: flex; gap: 1rem; }
.btn { padding: 0.7rem 1.5rem; border-radius: 6px; text-decoration: none; font-weight: 600; transition: all 0.2s; }
.btn-primary { background-color: var(--primary-color); color: white; border: 1px solid var(--primary-color); }
.btn-primary:hover { background-color: var(--primary-hover); }
.btn-outline { background-color: transparent; color: var(--text-main); border: 1px solid var(--border-color); background-color: var(--card-bg); }
.btn-outline:hover { border-color: var(--text-light); background-color: var(--bg-color); }

.grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(350px, 1fr)); gap: 1.5rem; }

footer { text-align: center; padding: 3rem 0; color: var(--text-light); font-size: 0.9rem; background-color: var(--card-bg); border-top: 1px solid var(--border-color); }

@media (max-width: 600px) {
  .hero h1 { font-size: 2.2rem; }
  .grid { grid-template-columns: 1fr; }
  .btn-group { flex-direction: column; }
  .btn { text-align: center; }
  .nav-links { display: none; }
}
</style>
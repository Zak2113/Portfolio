<template>
  <div class="card">
    <div class="card-header">
      <h3>{{ title }}</h3>
      <div class="project-links">
        <a :href="link" target="_blank">↗</a>
      </div>
    </div>
    <p>{{ description }}</p>
    <div class="tags">
      <span v-for="tag in tags" :key="tag" class="tag">{{ tag }}</span>
    </div>
  </div>
</template>

<script setup>
defineProps({
  title: String,
  description: String,
  link: String,
  tags: Array
})
</script>

<style scoped>
.card {
  background-color: var(--card-bg);
  border: 1px solid var(--border-color);
  border-radius: 12px;
  padding: 1.5rem;
  transition: transform 0.2s, box-shadow 0.2s;
  display: flex;
  flex-direction: column;
}
.card:hover {
  transform: translateY(-4px);
  box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.05);
  border-color: #cbd5e1;
}
.card-header {
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
  margin-bottom: 1rem;
}
.card h3 {
  font-size: 1.25rem;
  color: var(--text-main);
}
.project-links a {
  color: var(--text-light);
  text-decoration: none;
  font-size: 0.9rem;
  font-weight: 500;
}
.project-links a:hover {
  color: var(--primary-color);
  text-decoration: underline;
}
.card p {
  color: var(--text-light);
  font-size: 0.95rem;
  margin-bottom: 1.5rem;
  flex-grow: 1;
}
.tags {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
}
.tag {
  font-size: 0.75rem;
  font-weight: 600;
  color: var(--text-light);
  background-color: #f1f5f9;
  padding: 0.25rem 0.6rem;
  border-radius: 4px;
}
</style>
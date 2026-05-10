<template>
  <div class="experience-item">
    <div class="exp-top">
      <div class="exp-title">{{ role }}</div>
      <div class="exp-date">{{ date }}</div>
    </div>
    <div class="exp-company">{{ company }}</div>
    <ul>
      <li v-for="(bullet, index) in bullets" :key="index">{{ bullet }}</li>
    </ul>
  </div>
</template>

<script setup>
defineProps({
  role: String,
  company: String,
  date: String,
  bullets: Array
})
</script>

<style scoped>
.experience-item {
  background-color: var(--card-bg);
  border: 1px solid var(--border-color);
  border-radius: 12px;
  padding: 1.5rem;
  margin-bottom: 1rem;
}
.exp-top {
  display: flex;
  justify-content: space-between;
  margin-bottom: 0.5rem;
  flex-wrap: wrap;
}
.exp-title {
  font-weight: 700;
  font-size: 1.1rem;
}
.exp-date {
  color: var(--text-light);
  font-size: 0.9rem;
}
.exp-company {
  color: var(--primary-color);
  font-weight: 500;
  margin-bottom: 1rem;
  font-size: 0.95rem;
}
.experience-item ul {
  padding-left: 1.2rem;
  color: var(--text-light);
  font-size: 0.95rem;
}
.experience-item li {
  margin-bottom: 0.5rem;
}
</style>
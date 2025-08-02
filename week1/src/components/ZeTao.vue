<template>
  <div class="student-card">
    <div class="header">
      <h1 class="name">{{ name }}</h1>
      <div class="student-id">{{ studentId }}</div>
    </div>

    <div class="github">
      <a :href="github" target="_blank">
        {{ github }}
      </a>
    </div>

    <div class="info">
      <div class="item">
        <span>Course:</span> FIT5032
      </div>
      <div class="item">
        <span>Semester:</span> S2 2025
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ZeTao',
  data() {
    return {
      name: 'ZeTao Li',
      studentId: '34304525',
      github: 'https://github.com/AnInsomniacy/fit5032-homework'
    }
  }
}
</script>

<style scoped>
.student-card {
  max-width: 500px;
  margin: 2rem auto;
  background: linear-gradient(135deg, #4f46e5, #7c3aed);
  border-radius: 16px;
  padding: 2rem;
  color: white;
  box-shadow: 0 10px 30px rgba(0,0,0,0.2);
}

.header {
  text-align: center;
  margin-bottom: 2rem;
}

.name {
  font-size: 3rem;
  font-weight: bold;
  margin: 0 0 1rem 0;
  color: #fbbf24;
  text-shadow: 2px 2px 4px rgba(0,0,0,0.3);
}

.student-id {
  font-size: 1.5rem;
  font-weight: bold;
  background: rgba(255,255,255,0.2);
  padding: 0.8rem 1.5rem;
  border-radius: 12px;
  color: #34d399;
  font-family: 'Courier New', monospace;
  border: 2px solid rgba(255,255,255,0.3);
}

.github {
  background: rgba(255,255,255,0.1);
  border-radius: 12px;
  padding: 1.5rem;
  margin: 2rem 0;
  text-align: center;
}

.github a {
  color: white;
  text-decoration: none;
  font-size: 1.1rem;
  font-weight: 500;
  padding: 1rem;
  background: rgba(255,255,255,0.1);
  border-radius: 8px;
  display: inline-block;
  transition: all 0.3s ease;
  border: 1px solid rgba(255,255,255,0.2);
}

.github a:hover {
  background: rgba(255,255,255,0.2);
  transform: translateY(-2px);
}

.info {
  display: grid;
  gap: 1rem;
}

.item {
  background: rgba(255,255,255,0.1);
  padding: 1rem;
  border-radius: 8px;
  display: flex;
  justify-content: space-between;
}

.item span {
  font-weight: bold;
  color: #fbbf24;
}
</style>

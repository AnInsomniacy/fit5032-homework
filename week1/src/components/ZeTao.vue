<template>
  <div class="student-card">
    <div class="card-header">
      <div class="avatar">{{ initials }}</div>
      <div class="pulse-ring"></div>
    </div>

    <div class="card-content">
      <h1 class="student-name">{{ studentName }}</h1>
      <div class="student-number">ID: {{ studentNumber }}</div>

      <div class="info-grid">
        <div class="info-item">
          <span class="label">Course:</span>
          <span class="value">Vue.js Development</span>
        </div>
        <div class="info-item">
          <span class="label">Semester:</span>
          <span class="value">{{ currentSemester }}</span>
        </div>
        <div class="info-item">
          <span class="label">Status:</span>
          <span class="value status-active">Active</span>
        </div>
      </div>

      <div class="skills">
        <div class="skill-tag" v-for="skill in skills" :key="skill">
          {{ skill }}
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ZeTao',
  data() {
    return {
      studentName: 'ZeTao Li',
      studentNumber: '34304525',
      currentSemester: 'S2 2025',
      skills: ['Vue.js', 'JavaScript', 'HTML/CSS', 'Git']
    }
  },
  computed: {
    initials() {
      return this.studentName.split(' ').map(name => name[0]).join('')
    }
  }
}
</script>

<style scoped>
.student-card {
  max-width: 400px;
  margin: 2rem auto;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  border-radius: 20px;
  padding: 2rem;
  box-shadow: 0 20px 40px rgba(0,0,0,0.1);
  color: white;
  position: relative;
  overflow: hidden;
  animation: slideIn 0.8s ease-out;
}

.card-header {
  text-align: center;
  position: relative;
  margin-bottom: 2rem;
}

.avatar {
  width: 80px;
  height: 80px;
  border-radius: 50%;
  background: rgba(255,255,255,0.2);
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 2rem;
  font-weight: bold;
  margin: 0 auto;
  position: relative;
  z-index: 2;
  backdrop-filter: blur(10px);
}

.pulse-ring {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 80px;
  height: 80px;
  border: 3px solid rgba(255,255,255,0.3);
  border-radius: 50%;
  animation: pulse 2s infinite;
}

.student-name {
  font-size: 2.5rem;
  font-weight: 700;
  margin: 0;
  text-align: center;
  text-shadow: 2px 2px 4px rgba(0,0,0,0.3);
  animation: glow 2s ease-in-out infinite alternate;
}

.student-number {
  font-size: 1.2rem;
  text-align: center;
  margin: 0.5rem 0 2rem;
  opacity: 0.9;
  font-family: 'Courier New', monospace;
  background: rgba(255,255,255,0.1);
  padding: 0.5rem 1rem;
  border-radius: 10px;
  display: inline-block;
  width: 100%;
  box-sizing: border-box;
}

.info-grid {
  display: grid;
  gap: 1rem;
  margin: 2rem 0;
}

.info-item {
  display: flex;
  justify-content: space-between;
  padding: 0.75rem;
  background: rgba(255,255,255,0.1);
  border-radius: 10px;
  backdrop-filter: blur(5px);
}

.label {
  font-weight: 600;
  opacity: 0.8;
}

.value {
  font-weight: 500;
}

.status-active {
  color: #4ade80;
  font-weight: 700;
}

.skills {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
  justify-content: center;
  margin-top: 2rem;
}

.skill-tag {
  background: rgba(255,255,255,0.2);
  padding: 0.5rem 1rem;
  border-radius: 20px;
  font-size: 0.9rem;
  font-weight: 500;
  backdrop-filter: blur(5px);
  transition: transform 0.3s ease;
}

.skill-tag:hover {
  transform: translateY(-2px);
}

@keyframes slideIn {
  from {
    opacity: 0;
    transform: translateY(30px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

@keyframes pulse {
  0% {
    transform: translate(-50%, -50%) scale(1);
    opacity: 0.7;
  }
  50% {
    transform: translate(-50%, -50%) scale(1.1);
    opacity: 0.3;
  }
  100% {
    transform: translate(-50%, -50%) scale(1.2);
    opacity: 0;
  }
}

@keyframes glow {
  from {
    text-shadow: 2px 2px 4px rgba(0,0,0,0.3);
  }
  to {
    text-shadow: 2px 2px 20px rgba(255,255,255,0.5);
  }
}

@media (max-width: 480px) {
  .student-card {
    margin: 1rem;
    padding: 1.5rem;
  }

  .student-name {
    font-size: 2rem;
  }
}
</style>

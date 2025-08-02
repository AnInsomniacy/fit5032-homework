<template>
  <div id="app">
    <header class="app-header">
      <img alt="Vue logo" src="./assets/logo.png" class="logo">
      <h1>FIT5032 S2 2025 - Lab Assignment</h1>
    </header>

    <main>
      <ZeTao />
    </main>

    <footer class="app-footer">
      <p>Vue.js Development Course | Monash University</p>
    </footer>
  </div>
</template>

<script>
import ZeTao from './components/ZeTao.vue'

export default {
  name: 'App',
  components: {
    ZeTao
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  min-height: 100vh;
  background: linear-gradient(to bottom, #f8fafc, #e2e8f0);
}

.app-header {
  text-align: center;
  padding: 2rem 0;
  background: white;
  box-shadow: 0 2px 10px rgba(0,0,0,0.1);
}

.logo {
  width: 60px;
  height: 60px;
  margin-bottom: 1rem;
}

.app-header h1 {
  color: #2c3e50;
  margin: 0;
  font-size: 1.8rem;
  font-weight: 600;
}

main {
  padding: 2rem 0;
}

.app-footer {
  text-align: center;
  padding: 2rem;
  background: #2c3e50;
  color: white;
  margin-top: auto;
}

.app-footer p {
  margin: 0;
  opacity: 0.8;
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  margin: 0;
  background: #f8fafc;
}
</style>

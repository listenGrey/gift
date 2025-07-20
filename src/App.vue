<template>
  <div class="container">
    <Home />
  </div>
</template>

<script setup>
import Home from './views/Home.vue'
</script>

<style scoped>
html, body {
  margin: 0;
  padding: 0;
  font-size: 16px;
  font-family: 'Helvetica Neue', sans-serif;
  background-color: #fffaf4;
}

* {
  box-sizing: border-box;
}

.container {
  max-width: 420px;
  margin: 0 auto;
  padding: 1.5rem 1rem;
}

</style>

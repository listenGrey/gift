<template>
  <div class="gift-wrapper">
    <button @click="show = true" class="open-button">Open Your Gift 🎁</button>
    <transition name="fade">
      <div v-if="show" class="card">
        <p>
          This little world was made just for you.<br /><br />
          May it bring you the smile you deserve on your birthday.<br /><br />
          — from the guy who wishes he could give you this in person 🇬🇧
        </p>
      </div>
    </transition>
  </div>
</template>

<script setup>
import { ref } from 'vue'
const show = ref(false)
</script>

<style scoped>
.gift-wrapper {
  text-align: center;
  margin-top: 2rem;
}

.open-button {
  background-color: #ffb6b9;
  border: none;
  padding: 0.6rem 1.2rem;
  border-radius: 8px;
  font-size: 1rem;
  color: #fff;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.open-button:hover {
  background-color: #ff9ea2;
}

.card {
  background: #fff;
  border-radius: 12px;
  padding: 1.5rem;
  margin-top: 1.5rem;
  font-family: 'Georgia', serif;
  font-size: 1rem;
  line-height: 1.6;
  box-shadow: 0 0 10px rgba(0,0,0,0.1);
  max-width: 360px;
  margin-left: auto;
  margin-right: auto;
}

.fade-enter-active, .fade-leave-active {
  transition: opacity 0.6s ease;
}
.fade-enter-from, .fade-leave-to {
  opacity: 0;
}
</style>

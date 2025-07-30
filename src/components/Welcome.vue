<template>
  <div class="welcome">
    <canvas id="confetti-canvas" class="confetti-layer"></canvas>
    <h1>Happy Birthday, Pan🎉</h1>
    <img src="/cake.gif" alt="birthday cake" class="cake" />
    <div class="tips">
      <transition name="slide">
        <p v-if="showHint" class="hint">honey, press to continue ❤️</p>
      </transition>
    </div>
  </div>
</template>

<script setup>
import {onMounted, ref} from 'vue'
import confetti from 'canvas-confetti'

const showHint = ref(false)

onMounted(() => {
  setTimeout(() => {
    showHint.value = true
  }, 1000)

  const canvas = document.getElementById('confetti-canvas')
  const myConfetti = confetti.create(canvas, { resize: true, useWorker: true })

  myConfetti({
    particleCount: 500,
    spread: 60,
    origin: { x: 0, y: 0.4 },
    angle: 60
  })
  myConfetti({
    particleCount: 500,
    spread: 60,
    origin: { x: 1, y: 0.4 },
    angle: 120
  })
})
</script>

<style scoped>
.welcome {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-evenly;
  height: 93vh;
}

.confetti-layer {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  pointer-events: none;
  z-index: 0;
}

.welcome h1 {
  font-size: 2rem;
  opacity: 0.95;
  text-align: center;
  animation: fadeIn 3s ease forwards;
  color: #d2649a;
  margin-top: 3rem;
}

.cake {
  width: 100%;
}

.tips {
  font-size: 1.5rem;
  color: #888;
  text-align: center;
  height: 10vh;
}

.hint {
  animation: fadeInSlow 25s ease forwards;
}

.slide-enter-active, .slide-leave-active {
  transition: opacity 3s ease;
}
.slide-enter-from, .slide-leave-to {
  opacity: 0;
}

@keyframes fadeIn {
  from { opacity: 0; }
  to { opacity: 1; }
}
</style>

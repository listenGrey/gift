// FallingPetals.vue - 背景落花动画组件
<template>
  <div class="petal-container">
    <div v-for="n in 15" :key="n" class="petal" :style="randomStyle()"></div>
  </div>
</template>

<script setup>
function random(min, max) {
  return Math.random() * (max - min) + min
}

function randomStyle() {
  const delay = `${random(0, 5)}s`
  const duration = `${random(8, 14)}s`
  const left = `${random(0, 100)}vw`
  const size = `${random(14, 24)}px`
  return {
    left,
    animationDelay: delay,
    animationDuration: duration,
    width: size,
    height: size
  }
}
</script>

<style scoped>
.petal-container {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  overflow: hidden;
  pointer-events: none;
  z-index: 0;
}

.petal {
  position: absolute;
  top: -40px;
  background-image: url('/follower.png'); /* 建议用透明PNG的樱花花瓣图 */
  background-size: cover;
  background-repeat: no-repeat;
  opacity: 0.8;
  animation-name: fall;
  animation-timing-function: linear;
  animation-iteration-count: infinite;
}

@keyframes fall {
  0% {
    transform: translateY(0) rotate(0deg);
    opacity: 1;
  }
  100% {
    transform: translateY(100vh) rotate(360deg);
    opacity: 0;
  }
}
</style>

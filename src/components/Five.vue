<template>
  <div class="five">
    <div class="gift-box">
      💌<span class="tap-text">Tap to open my letter</span>
    </div>
  </div>
</template>

<script setup>
</script>

<style scoped>
.five {
  position: relative;
  min-height: 93vh;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  overflow: hidden;
}

.gift-box {
  font-size: 15rem;
  cursor: pointer;
  animation: pulse 1.8s infinite ease-in-out;
  position: relative;
  text-align: center;
}

.tap-text {
  display: block;
  font-size: 2rem;
  margin-top: 0.5rem;
  color: #a88;
  animation: fadein 2s ease-in-out infinite;
}

@keyframes pulse {
  0% { transform: scale(1); }
  50% { transform: scale(1.1); }
  100% { transform: scale(1); }
}

@keyframes fadein {
  0% { opacity: 0.2; }
  50% { opacity: 1; }
  100% { opacity: 0.2; }
}
</style>

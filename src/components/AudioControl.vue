// Step 6: AudioControl.vue - 背景音乐控制组件
<template>
  <div class="audio-control">
    <button @click="toggleMute">
      {{ isMuted ? '🔇' : '🎵' }}
    </button>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
const isMuted = ref(false)
let audioEl = null

onMounted(() => {
  audioEl = document.querySelector('audio')
  if (audioEl) audioEl.volume = 0.5
})

function toggleMute() {
  if (audioEl) {
    isMuted.value = !isMuted.value
    audioEl.muted = isMuted.value
  }
}
</script>

<style scoped>
.audio-control {
  position: fixed;
  top: 20px;
  right: 20px;
  z-index: 999;
}

.audio-control button {
  background: rgba(255, 255, 255, 0.8);
  border: none;
  font-size: 1.4rem;
  padding: 0.4rem 0.8rem;
  border-radius: 50%;
  box-shadow: 0 2px 6px rgba(0,0,0,0.15);
  cursor: pointer;
}
</style>

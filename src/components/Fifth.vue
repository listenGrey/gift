<template>
  <div class="fifth">
    <div class="gift-box" @click="openGift" v-if="!giftOpened">
      🎁<span class="tap-text">Tap to open your gift</span>
    </div>

    <transition name="fade">
      <div v-if="giftOpened" class="love-letter">
        <div class="letter-card">
          <Typewriter :text="letterText" />
        </div>
        <div class="particles">
          <span v-for="n in 20" :key="n" class="particle">✨</span>
        </div>
      </div>
    </transition>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import Typewriter from './Typewriter.vue'

const giftOpened = ref(false)
const letterText = `Dear Ploy,

I don’t know what you wished for this birthday,
but if it’s love, laughter, and someone who truly cares—
I hope I’m part of it.

You appeared quietly in my world,
but left behind noise in my heart.

So here I am—
sending you this little piece of me,
wrapped with a smile, sealed with warmth.

Happy Birthday again, my sunshine 🌤️`

function openGift() {
  giftOpened.value = true
}
</script>

<style scoped>
.fifth {
  position: relative;
  min-height: 100vh;
  background-color: #fffafc;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  overflow: hidden;
}

.gift-box {
  font-size: 4rem;
  cursor: pointer;
  animation: pulse 1.8s infinite ease-in-out;
  position: relative;
  text-align: center;
}

.tap-text {
  display: block;
  font-size: 1rem;
  margin-top: 0.5rem;
  color: #a88;
  animation: fadein 2s ease-in-out infinite;
}

.love-letter {
  text-align: center;
  padding: 2rem;
  position: relative;
}

.letter-card {
  background: #fff;
  padding: 2rem;
  border-radius: 16px;
  box-shadow: 0 0 20px rgba(0, 0, 0, 0.1);
  max-width: 90vw;
  font-size: 1.1rem;
  color: #444;
  white-space: pre-line;
}

.particles {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  pointer-events: none;
  overflow: hidden;
}

.particle {
  position: absolute;
  font-size: 1.5rem;
  color: #f5c1e2;
  animation: floatUp 2.5s ease-out infinite;
  left: calc(5% + 90% * var(--rand));
  top: 100%;
}

.particle:nth-child(odd) {
  animation-delay: 0.5s;
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

@keyframes floatUp {
  0% {
    opacity: 1;
    transform: translateY(0);
  }
  100% {
    opacity: 0;
    transform: translateY(-120px) scale(0.8);
  }
}

.fade-enter-active, .fade-leave-active {
  transition: opacity 1s ease;
}
.fade-enter-from, .fade-leave-to {
  opacity: 0;
}
</style>

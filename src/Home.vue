<template>
  <div class="container" @click="advance">
    <audio ref="audioRef" src="/music.mp3" autoplay loop hidden></audio>

    <transition name="fade">
      <div v-if="step === 1">
        <Welcome />
      </div>
    </transition>

    <transition name="fade">
      <div v-if="step === 2">
        <Typewriter :text="birthdayText" />
      </div>
    </transition>

    <transition name="fade">
      <div v-if="step === 3">
        <PhotoShow :photoUrl="photoUrl" />
        <DollImage :dollUrl="dollUrl" />
      </div>
    </transition>

    <transition name="fade">
      <div v-if="step === 4" class="center">
        <button @click.stop="openGift = true; step++" class="open-button">
          Tap to open your gift 🎁
        </button>
      </div>
    </transition>

    <transition name="fade">
      <div v-if="step === 5">
        <div class="card">
          <p>
            This little world was made just for you.<br /><br />
            May it bring you the smile you deserve on your birthday.<br /><br />
            — from the guy who wishes he could give you this in person 🇬🇧
          </p>
        </div>
        <FooterQuote />
      </div>
    </transition>
  </div>
</template>

<script setup>
import {onMounted, ref} from 'vue'
import Welcome from './components/Welcome.vue'
import Typewriter from './components/Typewriter.vue'
import PhotoShow from './components/PhotoShow.vue'
import DollImage from './components/DollImage.vue'
import FooterQuote from './components/FooterQuote.vue'

const birthdayText = `Dear Pan,\n\nYou once asked me if I liked dolls.\nMaybe this is my answer.\n\nHappy birthday, soft girl 🌸`
const photoUrl = '/src/assets/her.jpg'
const dollUrl = '/src/assets/doll.png'

const step = ref(1)
const openGift = ref(false)
const audioRef = ref(null)

onMounted(() => {
  audioRef.value?.play().catch(() => {})
})

function advance() {
  if (step.value < 5 && !openGift.value) {
    step.value++
  }
}

</script>

<style scoped>
.container {
  max-width: 450px;
  margin: 0 auto;
  padding: 2rem 1rem;
  position: relative;
  min-height: 100vh;
}

.center {
  text-align: center;
}

.open-button, .save-button {
  background-color: #ffb6b9;
  border: none;
  padding: 0.6rem 1.2rem;
  border-radius: 8px;
  font-size: 1rem;
  color: #fff;
  cursor: pointer;
  margin-top: 2rem;
  transition: background-color 0.3s ease;
}

.open-button:hover, .save-button:hover {
  background-color: #ff9ea2;
}

.fade-enter-active, .fade-leave-active {
  transition: opacity 1s ease;
}
.fade-enter-from, .fade-leave-to {
  opacity: 0;
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

@keyframes fadeIn {
  from { opacity: 0; }
  to { opacity: 1; }
}
</style>

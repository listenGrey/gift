<template>
  <div class="container" @click="advance">
    <audio ref="bgm" src="/bgm.mp3" autoplay loop preload="auto" style="display: none"/>

    <transition name="fade">
      <div class="sound-prompt" v-if="step === 1">
        <div class="dialog">
          <p>For the best experience,<br />please turn on your sound🎶</p>
          <button>OK</button>
        </div>
      </div>
    </transition>

    <transition name="fade">
      <div v-if="step === 2">
        <Welcome />
      </div>
    </transition>

    <transition name="fade">
      <div v-if="step === 3">
        <FallingPetals />
        <Second :text="secondText"  />
      </div>
    </transition>

    <transition name="fade">
      <div v-if="step === 4">
        <FallingPetals />
        <Third :text="thirdText"  />
      </div>
    </transition>

    <transition name="fade">
      <div v-if="step === 5">
        <FallingPetals />
        <Four :text="fourText" />
      </div>
    </transition>

    <transition name="fade">
      <div v-if="step === 6">
        <FallingPetals />
        <Seven :text="sevenText" />
      </div>
    </transition>

    <transition name="fade">
      <div v-if="step === 7">
        <FallingPetals />
        <Five />
      </div>
    </transition>

    <transition name="fade">
      <div v-if="step === 8">
        <FallingPetals />
        <Six />
      </div>
    </transition>

    <transition name="fade">
      <div v-if="step === 9">
        <Eight />
      </div>
    </transition>
  </div>
</template>

<script setup>
import { onMounted, ref } from 'vue'
import Welcome from './components/Welcome.vue'
import FallingPetals from './components/FallingPetals.vue'
import Second from './components/Second.vue'
import Third from './components/Third.vue'
import Four from './components/Four.vue'
import Five from './components/Five.vue'
import Six from './components/Six.vue'
import Seven from "./components/Seven.vue";
import Eight from './components/Eight.vue'

const secondText = `That day, I went to Coral Island.
I first saw you at the pier—under a gray sky, with the sea behind you.
And just like that, I got lucky.\n
In the heart of Phuket's rainy season,
I saw the clearest ocean...
and the brightest smile—yours.`

const thirdText = `That moment felt like the warmest part of my entire journey.
I took a photo of you—of you and the sea—
because some moments deserve to be held forever.\n
When we parted ways,
it felt like waking up from the most gentle dream.
And I... I didn't want to open my eyes.`

const fourText = `You once asked me,
“Do you like dolls?”

I smiled...
because the answer was already there, in front of me.

If you were a doll—
I wouldn't place you on a shelf,
or keep you behind glass.

I'd hold you gently,
laugh with you,
carry you everywhere my heart goes.

Because you...
you're the kind I'd never let go.`

const sevenText = `I heard you fell into the water,
and haven't been feeling well since...
My heart sank when I found out.

If I could, I'd be by your side—
wrapping you in the warmest towel,
bringing you tea,
whispering silly things just to make you smile.

Please take care of yourself, Pan.
You are too precious to be unwell.

Sending you healing thoughts from afar 🌸`

const step = ref(1)

onMounted(() => {
  const audio = document.querySelector('audio')

  const resumeAudio = () => {
    audio?.play().catch(() => {})
    document.removeEventListener('click', resumeAudio)
  }
  document.addEventListener('click', resumeAudio)
})

function advance() {
  if (step.value < 9 ) {
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

@keyframes fadeIn {
  from { opacity: 0; }
  to { opacity: 1; }
}

.sound-prompt {
  position: fixed;
  inset: 0;
  background: rgba(0, 0, 0, 0.75);
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 10000;
}

.dialog {
  background: white;
  padding: 24px 32px;
  border-radius: 12px;
  text-align: center;
  box-shadow: 0 0 20px rgba(255, 255, 255, 0.2);
}

.dialog p {
  font-size: 18px;
  margin-bottom: 16px;
}

.dialog button {
  background-color: #ff69b4;
  color: white;
  border: none;
  padding: 8px 20px;
  border-radius: 6px;
  cursor: pointer;
  font-size: 16px;
}
</style>

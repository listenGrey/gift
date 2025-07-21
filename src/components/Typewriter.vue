<template>
  <div class="typewriter">
    <p v-html="displayText"></p>
    <transition name="slide">
      <p v-if="showFinal" class="final-line">
        These are not just words. This is how I see you.
      </p>
    </transition>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const props = defineProps({ text: String })
const displayText = ref('')
const showFinal = ref(false)

const delay = (ms) => new Promise(resolve => setTimeout(resolve, ms))

onMounted(async () => {
  const fragments = props.text.split('\n')

  for (const line of fragments) {
    for (let i = 0; i < line.length; i++) {
      displayText.value += line[i]
      await delay(50)
    }
    displayText.value += '<br />'
    await delay(500) // 每句停顿 500ms
  }
  await delay(100)
  showFinal.value = true
})
</script>

<style scoped>
.typewriter {
  white-space: pre-wrap;
  font-family: 'Courier Prime', monospace;
  font-size: 1.1rem;
  color: #444;
  line-height: 1.7;
  text-align: center;
}

.highlight {
  color: #d2649a;
  font-weight: bold;
}

.final-line {
  margin-top: 1.5rem;
  font-style: italic;
  font-size: 0.95rem;
  color: #999;
  animation: fadeInSlow 5s ease forwards;
}

.slide-enter-active, .slide-leave-active {
  transition: opacity 1s ease;
}
.slide-enter-from, .slide-leave-to {
  opacity: 0;
}

@keyframes fadeInSlow {
  0% { opacity: 0; }
  100% { opacity: 1; }
}
</style>

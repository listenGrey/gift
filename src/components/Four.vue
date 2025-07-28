<template>
  <div class="four">
    <p v-html="displayText"></p>
    <transition name="slide">
      <img
          v-if="showFinal" class="pics"
          src="/doll.jpg"
      />
    </transition>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const props = defineProps({ text: String })
const displayText = ref('')
const showFinal = ref(false)
const visible = ref(false)

const delay = (ms) => new Promise(resolve => setTimeout(resolve, ms))

async function startTyping() {
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
}

onMounted(async () => {
  await delay(500)
  visible.value = true
  await delay(2000)
  await startTyping()
})
</script>

<style scoped>
.four {
  white-space: pre-wrap;
  font-family: 'Courier Prime', monospace;
  font-size: 1.1rem;
  color: #444;
  line-height: 1.7;
}

.pics {
  animation: fadeInSlow 5s ease forwards;
  width: 100%;
  height: 50%;
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

<template>
  <div class="five">
    <div class="gift-box">
      🎁<span class="tap-text" v-html="displayText"></span>
    </div>
  </div>
</template>

<script setup>
import {onMounted, ref} from "vue";

const props = defineProps({ text: String })
const displayText = ref('')
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
}

onMounted(async () => {
  await delay(500)
  visible.value = true
  await delay(2000)
  await startTyping()
})
</script>

<style scoped>
.five {
  position: relative;
  min-height: 93vh;
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
</style>

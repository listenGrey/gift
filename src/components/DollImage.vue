<template>
  <div class="doll-wrapper" v-show="visible">
    <img :src="dollUrl" alt="Doll" class="doll" />
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
const props = defineProps({ dollUrl: String })
const visible = ref(false)

onMounted(() => {
  setTimeout(() => {
    visible.value = true
  }, 3000) // 3秒后浮现，跟在照片之后
})
</script>

<style scoped>
.doll-wrapper {
  text-align: center;
  opacity: 0;
  transition: opacity 1.2s ease;
}

.doll-wrapper[style*="display: block"] {
  opacity: 1;
}

.doll {
  width: 60%;
  margin-top: 1.2rem;
  animation: float 3s ease-in-out infinite;
}

@keyframes float {
  0%, 100% { transform: translateY(0); }
  50% { transform: translateY(-10px); }
}
</style>

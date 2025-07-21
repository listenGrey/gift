// Step 5: FooterQuote.vue - 页面结尾金句组件
<template>
  <div class="footer-quote" v-show="visible">
    <p>This page will stay online forever, like this memory.</p>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
const visible = ref(false)

onMounted(() => {
  setTimeout(() => {
    visible.value = true
  }, 6000) // 延迟出现：等打字、照片、卡片之后
})
</script>

<style scoped>
.footer-quote {
  text-align: center;
  font-size: 0.95rem;
  font-style: italic;
  margin-top: 2.5rem;
  opacity: 0;
  transition: opacity 2s ease;
  color: #555;
}

.footer-quote[style*="display: block"] {
  opacity: 1;
}
</style>

<template>
  <div class="photo-wrapper" v-show="visible">
    <img src="/public/her.jpg" alt="Her" class="her-photo" />
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
const props = defineProps({ photoUrl: String })
const visible = ref(false)

onMounted(() => {
  setTimeout(() => {
    visible.value = true
  }, 2000) // 2 秒后渐显，配合打字结束
})
</script>

<style scoped>
.photo-wrapper {
  text-align: center;
  opacity: 0;
  transition: opacity 1.5s ease;
}

.photo-wrapper[style*="display: block"] {
  opacity: 1;
}

.her-photo {
  width: 100%;
  border-radius: 1rem;
  box-shadow: 0 0 12px rgba(0, 0, 0, 0.1);
  margin-top: 1.5rem;
}
</style>

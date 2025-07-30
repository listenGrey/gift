<template>
  <div class="eight">
    <h2 class="title">These memories belong to you 💖</h2>

    <div class="photo-stack">
      <img v-for="(photo, index) in photos" :key="index" :src="photo" class="photo" :style="getPhotoStyle(index)" />
    </div>

    <button class="download-btn" @click="downloadImages">
      Download Your HD Photos
    </button>
  </div>
</template>

<script setup>
const photos = [
  '/hdpics/DSC_0297.jpg',
  '/hdpics/DSC_0301.jpg',
  '/hdpics/DSC_0658.jpg',
  '/hdpics/DSC_0665.jpg',
  '/hdpics/DSC_0302.jpg'
]

const downloadPics = [
  '/hdpics/DSC_0661.jpg',
  '/hdpics/DSC_0298.jpg',
  '/hdpics/DSC_0297.jpg',
  '/hdpics/DSC_0301.jpg',
  '/hdpics/DSC_0302.jpg',
  '/hdpics/DSC_0658.jpg',
  '/hdpics/DSC_0665.jpg'
]

function getPhotoStyle(index) {
  const offset = index * 10
  const rotate = (index - 1) * 10
  return {
    transform: `translateY(-${offset}px) rotate(${rotate}deg)`
  }
}

function downloadImages() {
  downloadPics.forEach((photo, i) => {
    const a = document.createElement('a')
    a.href = photo
    a.download = `BeautifulPan${i + 1}.jpg`
    document.body.appendChild(a)
    a.click()
    document.body.removeChild(a)
  })
}
</script>

<style scoped>
.eight {
  min-height: 93vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-evenly;
}

.title {
  font-size: 1.8rem;
  font-family: 'Dancing Script', cursive;
  margin-bottom: 2rem;
  color: #333;
  text-align: center;
}

.photo-stack {
  position: relative;
  width: 240px;
  height: 200px;
  margin-bottom: 2rem;
}

.photo {
  position: absolute;
  width: 100%;
  height: auto;
  border-radius: 12px;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
  transition: transform 3s ease;
}

.download-btn {
  background: #ffb6c1;
  color: #fff;
  border: none;
  padding: 0.8rem 1.5rem;
  font-size: 1rem;
  border-radius: 10px;
  cursor: pointer;
  transition: background 0.3s;
}
.download-btn:hover {
  background: #ff9bb0;
}
</style>
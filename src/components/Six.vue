<template>
  <div class="six">
    <div class="love-letter">
      <div class="handwritten">
        <button class="lang-switch" @click.stop="toggleLang">{{ currentLang.toUpperCase() }}</button>
        <p class="handwritten" v-html="displayText" />
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'

const currentLang = ref('th')

const textByLang = {
  th: `Dear Pan,<br/><br/>
       I don’t know what you wished for this birthday.
       Maybe it was something small, like a piece of cake...
       or something quiet, like peace of mind.<br/><br/>

       But if, somewhere in your heart,
       you wished for love—
       real, gentle, and quietly fierce—
       then I hope... I'm part of that wish.<br/><br/>

       You walked into my life without warning.
       No grand entrance, no fireworks.
       Just a glance, a smile—
       and suddenly, there was sound in silence,
       warmth where I didn't know I was cold.<br/><br/>

       I think of you more often than I mean to.
       In still moments, in passing thoughts,
       in songs I never noticed before.<br/><br/>

       If I could wrap this note in a hug, I would.
       If I could fold myself into the paper,
       you’d feel my heartbeat through your fingertips.<br/><br/>

       This isn't just a birthday letter.
       It's a confession, a celebration,
       and a tiny promise wrapped in one.<br/><br/>

       Happy Birthday again, my sunshine.
       May your days be soft, your nights full of laughter,
       and your heart always safe.<br/><br/>

       Yours—gently, quietly, completely,<br/>
       Sebastian`,
  en: `ถึง แพน<br/><br/>

ฉันไม่รู้หรอกว่าคุณอธิษฐานอะไรไว้ในวันเกิดนี้
บางทีอาจเป็นเพียงเค้กชิ้นเล็ก ๆ
หรือเพียงความสงบใจในช่วงเวลาสั้น ๆ<br/><br/>

แต่ถ้าหัวใจของคุณได้แอบอธิษฐานถึงความรัก—
ความรักที่อ่อนโยน จริงใจ และลึกซึ้ง
ฉันหวังว่าฉันจะเป็นส่วนหนึ่งของคำนั้น<br/><br/>

คุณก้าวเข้ามาในชีวิตของฉันอย่างเงียบ ๆ
ไม่มีเสียง ไม่มีแสงไฟ
แค่รอยยิ้ม และสายตาคู่นั้น
ก็ทำให้โลกของฉันไม่เหมือนเดิมอีกเลย<br/><br/>

ฉันคิดถึงคุณบ่อยเกินกว่าที่จะยอมรับ
ทั้งในช่วงเวลาที่ว่างเปล่า ในเสียงเพลงที่เคยเฉยชา
หรือแม้แต่ในความเงียบที่เคยสงบ<br/><br/>

ถ้าฉันสามารถห่อจดหมายฉบับนี้ด้วยอ้อมกอดได้
ถ้าฉันสามารถพับหัวใจลงในกระดาษนี้
ฉันอยากให้คุณสัมผัสถึงการเต้นของหัวใจฉัน<br/><br/>

จดหมายฉบับนี้ไม่ใช่แค่คำอวยพรวันเกิด
แต่มันคือคำสารภาพเล็ก ๆ
คือการเฉลิมฉลอง
และคือคำสัญญาอันอ่อนหวาน<br/><br/>

สุขสันต์วันเกิดอีกครั้งนะ แสงแดดของฉัน
ขอให้ทุกวันของคุณนุ่มนวล คืนของคุณเต็มไปด้วยเสียงหัวเราะ
และหัวใจของคุณได้รับการปกป้องเสมอ<br/><br/>

จากใครบางคน… ที่เงียบ ๆ อ่อนโยน และเต็มไปด้วยความรู้สึก<br/>
Sebastian`
}

const displayText = computed(() => textByLang[currentLang.value])

function toggleLang() {
  currentLang.value = currentLang.value === 'th' ? 'en' : 'th'
}
</script>

<style scoped>
.six {
  position: relative;
  min-height: 93vh;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  overflow: hidden;
}

.love-letter {
  background: repeating-linear-gradient(
      #fffdf6,
      #fffdf6 30px,
      #aad0ff40 31px,
      #fffdf6 32px
  );
  border-radius: 16px;
  padding: 2rem 1rem;
  font-family: 'Dancing Script', cursive;
  font-size: 1.3rem;
  color: #333;
  margin: 0 auto;
  transform-origin: center;
  animation: slideOpen 2.5s ease forwards;
}

.handwritten {
  font-family: 'Dancing Script', cursive;
  font-size: 1.3rem;
  color: #333;
  line-height: 2rem;
  text-align: left;
}

.lang-switch {
  position: absolute;
  top: 1rem;
  right: 1.5rem;
  background: transparent;
  border: 2px solid #888;
  padding: 0.2rem 0.6rem;
  border-radius: 8px;
  font-size: 0.9rem;
  cursor: pointer;
  transition: 0.3s;
}

.lang-switch:hover {
  background: #eee;
}

@keyframes slideOpen {
  0% {
    transform: scale(0.6) rotateX(90deg);
    opacity: 0;
  }
  100% {
    transform: scale(1) rotateX(0);
    opacity: 1;
  }
}
</style>

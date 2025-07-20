<template>
  <div class="container">
    <Typewriter :text="birthdayMessage" />
    <!--<img src="@/assets/doll.png" alt="doll" class="doll" />-->
    <BirthdayCard />
    <!--<audio :src="music" autoplay loop />-->
  </div>
</template>

<script>
import Typewriter from '../components/Typewriter.vue'
import BirthdayCard from '../components/BirthdayCard.vue'
// import music from './../public/music.mp3'

export default {
  components: { Typewriter, BirthdayCard },
  data() {
    return {
      birthdayMessage: `Dear Ploy,

You once asked me if I liked dolls.
Maybe this is my answer.

Happy birthday, soft girl 🌸`,
      //music,
    }
  },
}
</script>

<style scoped>
.container {
  text-align: center;
  background: linear-gradient(#fff9f3, #ffe4e1);
  min-height: 100vh;
  padding: 2rem;
}
.doll {
  margin-top: 2rem;
  max-width: 300px;
  animation: float 3s ease-in-out infinite;
}
@keyframes float {
  0%, 100% { transform: translateY(0); }
  50% { transform: translateY(-10px); }
}
</style>

<template>
  <div class="typewriter">
    <p>{{ displayText }}</p>
  </div>
</template>

<script>
export default {
  props: ['text'],
  data() {
    return {
      displayText: '',
      index: 0,
    }
  },
  mounted() {
    this.typeText()
  },
  methods: {
    typeText() {
      if (this.index < this.text.length) {
        this.displayText += this.text[this.index]
        this.index++
        setTimeout(this.typeText, 80)
      }
    },
  },
}
</script>

<style scoped>
.typewriter p {
  font-size: 1.5rem;
  font-family: 'Courier New', Courier, monospace;
  white-space: pre-wrap;
}
</style>

<template>
  <div class="hello">
    <div class="colour-container" :style="styles"></div>
  </div>
</template>

<script>
export default {
  name: 'colour',
  props: {
    code: String
  },
  computed: {
    styles () {
      return `background: ${this.code};`;
    }
  }
}
</script>

<style scoped>
.colour-container {
  width: 6vw;
  height: 6vw;
  border-radius: 0.4vw;
}
</style>

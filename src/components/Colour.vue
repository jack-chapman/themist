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
  width: 100px;
  height: 100px;
  border-radius: 7px;
}
</style>

<template>
  <div class="container">
    <h3 :style="`color: ${colourList[0]}`">{{listName}}</h3>
    <div class="colour-container">
      <colour
        v-for="(colour, index) in colourList"
        :key="index"
        :code="colour"
        class="space"
        :class="{'bigger': index === 4}"
      />
    </div>
  </div>
</template>

<script>
import Colour from './Colour.vue'
import chroma from 'chroma-js'

export default {
  name: 'colour-list',
  props: {
    baseColour: String,
    isNeutral: Boolean,
    listName: String
  },
  components: {
    Colour
  },
  watch: {
    colourList: {
      immediate: true,
      handler(value) {
        const payload = {
          name: this.listName,
          list: value
        }
        this.$emit('list', payload)
      }
    }
  },
  computed: {
    colourList() {
      const darkest = chroma(this.baseColour).darken(2.6)
      const lightest = this.isNeutral
        ? chroma(this.baseColour).brighten(2.3).desaturate(0.5)
        : chroma(this.baseColour).brighten(3)
      return chroma
        .scale([darkest, lightest])
        .mode('lab')
        .correctLightness()
        .colors(9, 'hex');
    }
  }
}
</script>

<style scoped>
h3 {
  font-family: sans-serif;
  text-align: left;
  margin-left: 10px;
}

.container {
  display: flex;
  flex-direction: column;
}
.colour-container {
  display: flex;
}
.space {
  margin: 5px;
}
.bigger {
  transform: scale(1.1);
  margin-left: 10px;
  margin-right: 10px;
}
</style>
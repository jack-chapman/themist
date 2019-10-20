<template>
  <div id="app">
    <colour-list v-for="(colour, index) in baseColours"
      :list-name="colour.name"
      :base-colour="colour.code"
      :is-neutral="colour.isNeutral"
      :key="index"
      @list="updateList"
    />
    <styles-block
      :primary="primaryColours"
      :accent="accentColours"
      :neutral="neutralColours"
      :destructive="destructiveColours"
      :warning="warningColours"
      :positive="positiveColours"
    />
  </div>
</template>

<script>
import ColourList from './components/ColourList.vue'
import StylesBlock from './components/StylesBlock.vue'

export default {
  name: 'app',
  components: {
    ColourList,
    StylesBlock
  },
  data() {
    return {
      baseColours: [
        {
          name: 'Primary',
          code: '#8719E0',
          isNeutral: false
        },
        {
          name: 'Accent',
          code: '#27AB83',
          isNeutral: false
        },
        {
          name: 'Neutral',
          code: '#627D98',
          isNeutral: true
        },
        {
          name: 'Destructive',
          code: '#E12D39',
          isNeutral: false
        },
        {
          name: 'Warning',
          code: '#F0B429',
          isNeutral: false
        },
        {
          name: 'Positive',
          code: '#2BB0ED',
          isNeutral: false
        },
      ],
      primaryColours: [],
      accentColours: [],
      neutralColours: [],
      destructiveColours: [],
      warningColours: [],
      positiveColours: [],
    }
    
  },
  methods: {
    updateList(value) {
      switch (value.name) {
        case 'Primary':
          this.primaryColours = value.list;
          break;
        case 'Accent':
          this.accentColours = value.list;
          break;
        case 'Neutral':
          this.neutralColours = value.list;
          break;
        case 'Destructive':
          this.destructiveColours = value.list;
          break;
        case 'Warning':
          this.warningColours = value.list;
          break;
        case 'Positive':
          this.positiveColours = value.list;
          break;
        default:
          break;
      }
    }
  }
}
</script>

<style>
#app {
  display: flex;
  flex-direction: column;
  align-items: center;
}
.space {
  margin: 5px;
}
</style>

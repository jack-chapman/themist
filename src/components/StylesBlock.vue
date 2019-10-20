<template>
  <div class="container" :style="`background:${neutral[8]};color:${neutral[0]}`">
    <code style="margin:0;">
<pre style="margin:0;">
:root {<template v-for="(colour, index) in primary">
  --primary-{{index}}: {{colour}};</template>
<template v-for="(colour, index) in accent">
  --accent-{{index}}: {{colour}};</template>
<template v-for="(colour, index) in neutral">
  --neutral-{{index}}: {{colour}};</template>
<template v-for="(colour, index) in destructive">
  --destructive-{{index}}: {{colour}};</template>
<template v-for="(colour, index) in warning">
  --warning-{{index}}: {{colour}};</template>
<template v-for="(colour, index) in positive">
  --positive-{{index}}: {{colour}};</template>
}
</pre>
    </code>
  </div>
</template>

<script>
export default {
  name: 'styles-block',
  props: {
    primary: Array,
    accent: Array,
    neutral: Array,
    destructive: Array,
    warning: Array,
    positive: Array,
  }
}
</script>

<style scoped>
.container {
  border-radius: 7px;
  padding: 10px 20px;
  margin-top: 30px;
  margin-left: 5px;
  width: auto;
}
</style>
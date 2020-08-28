<template>
  <div class="timeline" :class="{'reverse': reverse}">
    <slot />
  </div>
</template>

<script>
export default {
  name: 'el-horizontal-timeline',

  props: {
    "reverse": Boolean
  }
}
</script>

<style scoped>
.timeline {
  margin-left: 1.3em;
  margin-right: 1.3em;
  align-content: center;
  align-items: center;
  counter-reset: stepCount;
  display: flex;
  justify-content: space-around;
  font-size: 1.3em;
  background-color: rgb(230, 171, 171);
  z-index: -2;
}

.reverse {
  flex-direction: row-reverse;
}
</style>
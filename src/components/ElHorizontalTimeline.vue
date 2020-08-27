<template>
  <div class="timeline">
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
  margin-left: 10px;
  align-content: center;
  align-items: center;
  counter-reset: stepCount;
  display: flex;
  justify-content: space-around;
  font-size: 1.3em;
}
</style>
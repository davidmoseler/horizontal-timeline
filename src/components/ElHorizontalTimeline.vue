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
  counter-reset: stepCount;
  display: flex;
}

.reverse {
  flex-direction: row-reverse;
}
</style>
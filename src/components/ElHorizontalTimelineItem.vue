<template>
  <div>
    <div class="timeline-item">
    </div>
    <div v-if="placement == 'top'">
      <p v-if="!hideTimestamp">{{timestamp}}</p>
      <slot />
    </div>
    <div v-else>
      <slot />
      <p v-if="!hideTimestamp">{{timestamp}}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'el-horizontal-timeline-item',

  props: {
    "timestamp": String,
    "hide-timestamp": Boolean,
    "placement": String,
    "type": String,
    "color": String,
    "size": String,
    "icon": String

  }
}
</script>

<style scoped>
.timeline-item {
  background: dodgerblue;
  color: white;
  content: ' ';
  display: flex;
  flex-grow: 1;
  height: .3em;
  line-height: 1em;
  margin: 0;
  position: relative;
  text-align: right;
  z-index: -1;
}
.timeline-item::before {
  color: white;
  background: dodgerblue;
  border-radius: 50%;
  counter-increment: stepCount;
  content: counter(stepCount); 
  height: 2em;
  left: 0em;
  right: 0em;
  line-height: 2em;
  position: absolute;
  text-align: center;
  top: -.85em;
  width: 2em;
}
.timeline-item.active {
  background-color: lightblue;
}
.timeline-item.active ~ .timeline-item {
  background-color: lightblue;
}
.timeline-item.active ~ .timeline-item::before {
  background-color: lightblue;
}
.timeline-item:last-child {
  flex-basis: 0;
  flex-grow: 0;
  flex-shrink: 1;
  right: 2em;
}
.timeline.highlight-active .timeline-item.active::before {
  font-size: 1.6em;
  background: maroon;
}
</style>
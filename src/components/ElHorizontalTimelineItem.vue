<template>
  <div class="flexpurposes">
    <template v-if="placement == 'top'">
      <p v-if="!hideTimestamp">{{timestamp}}</p>
      <el-tooltip content="Tooltip">
        <div :class="{
          'timeline-item': size == 'normal',
          'timeline-item-large': size == 'large',
          'numbered-node': icon == undefined
        }">
          <div>
            <i v-if="icon" :class="[icon]" />
          </div>
        </div>
      </el-tooltip>
    </template>
    <template v-else>
      <el-tooltip :content="content">
        <div :class="{
          'timeline-item': size == 'normal',
          'timeline-item-large': size == 'large',
          'numbered-node': icon == undefined
        }">
          <div>
            <i v-if="icon" :class="[icon]" />
          </div>
        </div>
      </el-tooltip>
      <p v-if="!hideTimestamp">{{timestamp}}</p>
    </template>
  </div>
</template>

<script>
import 'element-ui/lib/theme-chalk/index.css';

export default {
  name: 'el-horizontal-timeline-item',

  props: {
    "timestamp": String,
    "hide-timestamp": Boolean,
    "placement": String,
    "type": String,
    "color": String,
    "size": {
      type: String,
      default : 'normal'
    },
    "icon": String
  },
  computed: {
    content() {
      return this.$slots.default[0].text
    }
  }
}
</script>

<style scoped>
.flexpurposes {
  flex-grow: 1;
}
.timeline-item {
  color: white;
  content: ' ';
  display: flex;
  /* height: .3em; */
  line-height: 1em;
  margin: 0;
  text-align: right;
  justify-content: center;
  position: relative;
}
.timeline-item div {
  color: white;
  background: dodgerblue;
  border-radius: 50%;
  height: 2em;
  left: 0em;
  right: 0em;
  line-height: 2em;
  text-align: center;
  top: -.85em;
  width: 2em;
  z-index: 1;
}
.timeline-item::before{
  color: white;
  background: dodgerblue;
  height: .3em;
  text-align: center;
  position: absolute;
  top: 0.85em;
  width: 100%;
  content: "";
}
.flexpurposes:first-child .timeline-item::before {
  width: 50%;
  left: 50%;
}
.flexpurposes:last-child .timeline-item::before {
  width: 50%;
  right: 50%;
}
.numbered-node div {
  counter-increment: stepCount;
}
.numbered-node div::before {
  content: counter(stepCount);
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
p {
  margin: 5px;
}
i {
  position: relative;
}
</style>
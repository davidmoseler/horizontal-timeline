<template>
  <div class="timeline-item" :style="cssVars">
    <p v-if="!hideTimestamp && placement == 'top'">{{timestamp}}</p>
    <el-tooltip :content="content">
      <div :class="{
        'node': true,
        'numbered-node': icon == undefined
      }">
        <div>
          <i v-if="icon" :class="[icon]" />
        </div>
      </div>
    </el-tooltip>
    <p v-if="!hideTimestamp && placement == 'bottom'">{{timestamp}}</p>
  </div>
</template>

<script>
import 'element-ui/lib/theme-chalk/index.css';

export default {
  name: 'el-horizontal-timeline-item',

  props: {
    "timestamp": String,
    "hide-timestamp": Boolean,
    "placement": {
      type: String,
      default: 'bottom'
    },
    "type": String,
    "color": {
      type: String,
      default: 'lightgrey'
    },
    "size": {
      type: String,
      default: 'normal'
    },
    "icon": String
  },
  computed: {
    content() {
      return this.$slots.default[0].text
    },
    cssVars() {
      let nodeSize;
      if(this.size == 'normal'){
        nodeSize = '2em'
      } else {
        nodeSize = '3em'
      }
      return {
        '--node-size': nodeSize,
        '--node-color': this.color
      }
    }
  }
}
</script>

<style scoped>
.timeline-item {
  flex-grow: 1;
}
.node {
  display: flex;
  justify-content: center;
  position: relative;
}
.node div {
  color: white;
  background: var(--node-color);
  border-radius: 50%;
  text-align: center;
  line-height: var(--node-size);
  width: var(--node-size);
  z-index: 1;
}
.node::before{
  color: white;
  background: lightgrey;
  height: .3em;
  text-align: center;
  position: absolute;
  top: calc(var(--node-size)/2 - .15em);
  width: 100%;
  content: "";
}
.timeline-item:first-child .node::before {
  width: 50%;
  left: 50%;
}
.timeline-item:last-child .node::before {
  width: 50%;
  right: 50%;
}
.numbered-node div {
  counter-increment: stepCount;
}
.numbered-node div::before {
  content: counter(stepCount);
}
p {
  margin: .3em;
  color: lightgrey;
  font-weight: bold;
}
</style>
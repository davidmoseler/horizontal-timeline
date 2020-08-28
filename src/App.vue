<template>
  <div id="app">
    <el-horizontal-timeline>
      <el-horizontal-timeline-item 
        v-for="(activity, i) in activities"
        :key="i"
        :timestamp="activity.timestamp"
        icon="el-icon-delete"
      >
        {{activity.content}}
      </el-horizontal-timeline-item>
    </el-horizontal-timeline>
  </div>
</template>

<script>
import ElHorizontalTimeline from './components/ElHorizontalTimeline.vue'
import ElHorizontalTimelineItem from './components/ElHorizontalTimelineItem.vue'

export default {
  name: 'App',
  components: {
    ElHorizontalTimeline,
    ElHorizontalTimelineItem
  },

  data (){
    return {
      activities: [{
        content: 'Event start',
        timestamp: '2018-04-15'
      }, {
        content: 'Approved',
        timestamp: '2018-04-13'
      }, {
        content: 'Success',
        timestamp: '2018-04-11'
      }]
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

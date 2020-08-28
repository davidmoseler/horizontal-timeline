<script>
export default {
  name: 'el-horizontal-timeline',

  props: {
    "reverse": Boolean
  },
  render(createElement) {
    let items = this.$slots.default
    if(this.reverse){
      items = items.reverse()
    }
    return createElement(
      'div',
      {
        class: {
          'timeline': true
        }
      },
      items
    )
  }
}

</script>

<style scoped>
.timeline {
  counter-reset: stepCount;
  display: flex;
  text-align: center;
  align-items: center;
}
</style>
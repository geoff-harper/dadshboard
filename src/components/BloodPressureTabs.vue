<template>
  <nav class="blood-pressure__tabs">
    <ul>
      <li @click="changeView">Table</li>
      <li @click="changeView">Graph</li>
      <li>Export Data</li>
    </ul>
  </nav>
</template>

<script>
export default {
  name: 'BloodPressureTabs',
  data () {
    return {}
  },
  methods: {
    changeView (e) {
      const tab = e.target.innerHTML
      if (tab === 'Table') this.$emit('changeView', 0) // Table
      else this.$emit('changeView', 1) // Graph
    }
  }
}
</script>

<style lang="scss">
@import '~vars';

.blood-pressure__tabs {
  flex: 1 0 auto;
  padding-bottom: 20px;

  ul {
    display: flex;
    flex-flow: row nowrap;

    li {
      flex: 1 0 33%;
      padding: 20px 10px;
      text-align: center;
      border-right: 1px solid $border-colour;

      &:last-child {
        border: none;
      }
    }
  }
}
</style>

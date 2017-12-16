<template>
  <nav class="blood-pressure__tabs">
    <ul>
      <li @click="changeView">Table</li>
      <li @click="changeView">Graph</li>
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

<style>
.blood-pressure__tabs ul {
  display: flex;
  flex-flow: row nowrap;
}
.blood-pressure__tabs ul li {
  flex: 1 0 50%;
  padding: 20px 10px;
  text-align: center;
}
.blood-pressure__tabs ul li:first-child {
  border-right: 1px solid #DDD;
}
</style>

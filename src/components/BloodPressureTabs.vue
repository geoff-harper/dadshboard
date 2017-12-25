<template>
  <nav class="blood-pressure__tabs">
    <ul>
      <li :class="['blood-pressure__tab', activeView === 0 ? 'active' : null]" @click="changeView">Table</li>
      <li :class="['blood-pressure__tab', activeView === 1 ? 'active' : null]" @click="changeView">Graph</li>
      <li class="blood-pressure__tab">Export Data</li>
    </ul>
  </nav>
</template>

<script>
export default {
  name: 'BloodPressureTabs',
  data () {
    return {
      activeView: 0
    }
  },
  methods: {
    changeView (e) {
      const tab = e.target.innerHTML
      if (tab === 'Table') this.activeView = 0 // Table
      else this.activeView = 1 // Graph
      this.$emit('changeView', this.activeView)
    }
  }
}
</script>

<style lang="scss">
@import '~vars';
@import '~mixins';

  
.blood-pressure__tabs {
  padding-bottom: 10px;

  .blood-pressure__tab {
    padding: 10px;
    text-align: center;
    border-bottom: 1px solid $border-colour;
    cursor: pointer;
    font-weight: 600;

    @include on-event() {
      background-color: $second-colour;
      color: $white;
    }

    &.active {
      background-color: $primary-colour;
      color: $white;
    }
  }
}
  
@include bp(md) {
  .blood-pressure__tabs {
    flex: 1 0 auto;

    ul {
      display: flex;
      flex-flow: row nowrap;

      .blood-pressure__tab {
        flex: 1 0 33%;
        border: 1px solid $border-colour;

        &:first-child {
          border-left: none;
        }

        &:last-child {
          border-right: none;
        }
      }
    }
  }
}
</style>

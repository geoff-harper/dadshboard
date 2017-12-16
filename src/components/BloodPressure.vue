<template>
  <section id="blood-pressure" class="card card--small-view">
    <BloodPressureTabs @changeView="changeView"></BloodPressureTabs>
    <figure class="blood-pressure__data-view" ref="chartContainer">
      <BloodPressureTable v-if="view === 0" :heartData="heartData"></BloodPressureTable>
      <vue-c3 v-show="view === 1" :handler="handler"></vue-c3>
    </figure>
    <BloodPressureInput @add="addVariation"></BloodPressureInput>
  </section>
</template>

<script>
import Vue from 'vue'
import VueC3 from 'vue-c3'
import VueC3CSS from '../assets/c3.min.css' // eslint-disable-line

import BloodPressureInput from './BloodPressureInput'
import BloodPressureTabs from './BloodPressureTabs'
import BloodPressureTable from './BloodPressureTable'

export default {
  name: 'BloodPressure',
  components: {
    VueC3,
    BloodPressureTabs,
    BloodPressureInput,
    BloodPressureTable
  },
  data () {
    return {
      view: 0, // Table = 0, Graph = 1
      handler: new Vue(),
      heartData: {
        xAxis: ['2017-12-01 07:45', '2017-12-02 07:45', '2017-12-03 07:45', '2017-12-04 07:45', '2017-12-05 07:45', '2017-12-06 07:45', '2017-12-07 07:45', '2017-12-08 07:45', '2017-12-09 07:45'],
        systolicVals: [132, 129.5, 127.5, 138, 128, 138, 138, 124, 129.5],
        dystolicVals: [88, 80.5, 81.5, 87, 81.5, 85, 88, 83.5, 84],
        pulseVals: [62, 63.5, 71.5, 70.5, 68, 70, 65.5, 61.5, 69]
      }
    }
  },
  methods: {
    addVariation () {},
    changeView (view) {
      this.view = view
    }
  },
  mounted () {
    const containerHeight = this.$refs.chartContainer.clientHeight
    const options = {
      data: {
        x: 'x',
        xFormat: '%Y-%m-%d %H:%M',
        columns: [
          ['x', ...this.heartData.xAxis],
          ['Systolic', ...this.heartData.systolicVals],
          ['Dystolic', ...this.heartData.dystolicVals],
          ['Pulse', ...this.heartData.pulseVals]
        ]
      },
      axis: {
        x: {
          type: 'timeseries',
          tick: {
            format: '%Y-%m-%d %H:%M',
            outer: false
          }
        },
        y: {
          tick: {
            outer: false
          }
        }
      },
      size: {
        height: containerHeight
      },
      padding: {
        right: 30,
        left: 25
      }
    }
    this.handler.$emit('init', options)
  }
}
</script>

<style>
.c3-axis-x g.tick {
  display: none;
}
section#blood-pressure {
  display: flex;
  flex-flow: column nowrap;
  justify-content: space-between;
  align-items: stretch;
}
.blood-pressure__tabs {
  flex: 1 0 auto;
}
.blood-pressure__data-view {
  flex: 1 1 80%;
}
</style>

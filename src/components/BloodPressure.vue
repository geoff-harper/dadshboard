<template>
  <section id="blood-pressure" class="card card--small-view">
    <h1 class="card__title">Blood Pressure</h1>
    <BloodPressureTabs @changeView="changeView"></BloodPressureTabs>
    <figure :class="[view === 0 ? 'blood-pressure__data-view--table' : null, 'blood-pressure__data-view']" ref="chartContainer">
      <BloodPressureTable v-if="view === 0" :heartData="heartData"></BloodPressureTable>
      <vue-c3 v-show="view === 1" :handler="chartHandler" class="blood-pressure__graph"></vue-c3>
    </figure>
    <BloodPressureInput @add="addReading"></BloodPressureInput>
  </section>
</template>

<script>
import Vue from 'vue'
import VueC3 from 'vue-c3'
import '../assets/c3.min.css'

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
      chartHandler: new Vue(),
      heartData: [
        {
          date: '2017-12-01',
          time: '19:45',
          systolic: '132.0',
          diastolic: '88.0',
          pulse: '62.0'
        },
        {
          date: '2017-12-02',
          time: '19:45',
          systolic: '129.5',
          diastolic: '80.0',
          pulse: '63.5'
        },
        {
          date: '2017-12-03',
          time: '19:45',
          systolic: '127.5',
          diastolic: '81.5',
          pulse: '71.5'
        },
        {
          date: '2017-12-04',
          time: '19:45',
          systolic: '138.0',
          diastolic: '88.0',
          pulse: '70.5'
        },
        {
          date: '2017-12-05',
          time: '19:45',
          systolic: '128.0',
          diastolic: '87.0',
          pulse: '68.0'
        },
        {
          date: '2017-12-06',
          time: '19:45',
          systolic: '138.0',
          diastolic: '81.5',
          pulse: '70.0'
        },
        {
          date: '2017-12-07',
          time: '19:45',
          systolic: '138.0',
          diastolic: '85.0',
          pulse: '65.5'
        },
        {
          date: '2017-12-08',
          time: '19:45',
          systolic: '124.0',
          diastolic: '83.5',
          pulse: '61.5'
        },
        {
          date: '2017-12-01',
          time: '19:45',
          systolic: '132.0',
          diastolic: '88.0',
          pulse: '62.0'
        },
        {
          date: '2017-12-02',
          time: '19:45',
          systolic: '129.5',
          diastolic: '80.5',
          pulse: '63.5'
        },
        {
          date: '2017-12-03',
          time: '19:45',
          systolic: '127.5',
          diastolic: '81.5',
          pulse: '71.5'
        },
        {
          date: '2017-12-04',
          time: '19:45',
          systolic: '138.0',
          diastolic: '88.0',
          pulse: '70.5'
        },
        {
          date: '2017-12-05',
          time: '19:45',
          systolic: '128.0',
          diastolic: '87.0',
          pulse: '68.0'
        },
        {
          date: '2017-12-06',
          time: '19:45',
          systolic: '138.0',
          diastolic: '81.5',
          pulse: '70.0'
        },
        {
          date: '2017-12-07',
          time: '19:45',
          systolic: '138.0',
          diastolic: '85.0',
          pulse: '65.5'
        },
        {
          date: '2017-12-08',
          time: '19:45',
          systolic: '124.0',
          diastolic: '83.5',
          pulse: '61.5'
        },
        {
          date: '2017-12-01',
          time: '19:45',
          systolic: '132.0',
          diastolic: '88.0',
          pulse: '62.0'
        },
        {
          date: '2017-12-07',
          time: '19:45',
          systolic: '138.0',
          diastolic: '85.0',
          pulse: '65.5'
        },
        {
          date: '2017-12-08',
          time: '19:45',
          systolic: '124.0',
          diastolic: '83.5',
          pulse: '61.5'
        },
        {
          date: '2017-12-01',
          time: '19:45',
          systolic: '132.0',
          diastolic: '88.0',
          pulse: '62.0'
        },
        {
          date: '2017-12-08',
          time: '19:45',
          systolic: '124.0',
          diastolic: '83.5',
          pulse: '61.5'
        },
        {
          date: '2017-12-01',
          time: '19:45',
          systolic: '132.0',
          diastolic: '88.0',
          pulse: '62.0'
        },
        {
          date: '2017-12-08',
          time: '19:45',
          systolic: '124.0',
          diastolic: '83.5',
          pulse: '61.5'
        },
        {
          date: '2017-12-01',
          time: '19:45',
          systolic: '132.0',
          diastolic: '88.0',
          pulse: '62.0'
        }
      ]
    }
  },
  methods: {
    addReading (reading) {
      this.heartData.push(reading)

      const graphData = this.getGraphData()
      this.chartHandler.$emit('dispatch', (chart) => {
        chart.load({
          columns: [
            ['x', ...graphData.xAxis],
            ['Systolic', ...graphData.systolicVals],
            ['Diastolic', ...graphData.diastolicVals],
            ['Pulse', ...graphData.pulseVals]
          ]
        })
      })
    },
    getGraphData () {
      const graphData = {
        xAxis: [],
        systolicVals: [],
        diastolicVals: [],
        pulseVals: []
      }

      for (let reading of this.heartData) {
        // let formattedTime = reading.time.slice(0, -3)
        graphData.xAxis.push(`${reading.date} ${reading.time}`)
        graphData.systolicVals.push(reading.systolic)
        graphData.diastolicVals.push(reading.diastolic)
        graphData.pulseVals.push(reading.pulse)
      }

      return graphData
    },
    changeView (view) {
      this.view = view
    }
  },
  mounted () {
    const containerHeight = this.$refs.chartContainer.clientHeight
    const graphData = this.getGraphData()
    const options = {
      data: {
        x: 'x',
        xFormat: '%Y-%m-%d %H:%M',
        columns: [
          ['x', ...graphData.xAxis],
          ['Systolic', ...graphData.systolicVals],
          ['Diastolic', ...graphData.diastolicVals],
          ['Pulse', ...graphData.pulseVals]
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
    this.chartHandler.$emit('init', options)
  }
}
</script>

<style lang="scss">
@import '~vars';

section#blood-pressure {
  display: flex;
  flex-flow: column nowrap;
  justify-content: space-between;
  align-items: stretch;
  grid-column: 1 / span 2;
  grid-row: 1 / 2;
}

.blood-pressure__data-view {
  flex: 1 1 80%;
  max-height: 40vh;

  &--table {
    overflow-y: scroll;
    overflow-x: hidden;
  }
}

.blood-pressure__graph {
  .c3-axis-x g.tick {
    display: none;
  }
  .c3-axis-x g.tick {
    fill: $border-colour
  }
  .c3-axis path,
  .c3-axis line {
    stroke: $border-colour
  }
}
</style>

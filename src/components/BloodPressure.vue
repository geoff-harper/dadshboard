<template>
  <section id="blood-pressure" class="card card--small-view">
    <BloodPressureTabs @changeView="changeView"></BloodPressureTabs>
    <figure :class="[view === 0 ? 'blood-pressure__data-view--table' : null, 'blood-pressure__data-view']" ref="chartContainer">
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
      heartData: [
        {
          date: '2017/12/01',
          time: '07:45',
          systolic: '132',
          dystolic: '88',
          pulse: '62'
        },
        {
          date: '2017/12/02',
          time: '07:45',
          systolic: '129.5',
          dystolic: '80.5',
          pulse: '63.5'
        },
        {
          date: '2017/12/03',
          time: '07:45',
          systolic: '127.5',
          dystolic: '81.5',
          pulse: '71.5'
        },
        {
          date: '2017/12/04',
          time: '07:45',
          systolic: '138',
          dystolic: '88',
          pulse: '70.5'
        },
        {
          date: '2017/12/05',
          time: '07:45',
          systolic: '128',
          dystolic: '87',
          pulse: '68'
        },
        {
          date: '2017/12/06',
          time: '07:45',
          systolic: '138',
          dystolic: '81.5',
          pulse: '70'
        },
        {
          date: '2017/12/07',
          time: '07:45',
          systolic: '138',
          dystolic: '85',
          pulse: '65.5'
        },
        {
          date: '2017/12/08',
          time: '07:45',
          systolic: '124',
          dystolic: '83.5',
          pulse: '61.5'
        },
        {
          date: '2017/12/01',
          time: '07:45',
          systolic: '132',
          dystolic: '88',
          pulse: '62'
        },
        {
          date: '2017/12/02',
          time: '07:45',
          systolic: '129.5',
          dystolic: '80.5',
          pulse: '63.5'
        },
        {
          date: '2017/12/03',
          time: '07:45',
          systolic: '127.5',
          dystolic: '81.5',
          pulse: '71.5'
        },
        {
          date: '2017/12/04',
          time: '07:45',
          systolic: '138',
          dystolic: '88',
          pulse: '70.5'
        },
        {
          date: '2017/12/05',
          time: '07:45',
          systolic: '128',
          dystolic: '87',
          pulse: '68'
        },
        {
          date: '2017/12/06',
          time: '07:45',
          systolic: '138',
          dystolic: '81.5',
          pulse: '70'
        },
        {
          date: '2017/12/07',
          time: '07:45',
          systolic: '138',
          dystolic: '85',
          pulse: '65.5'
        },
        {
          date: '2017/12/08',
          time: '07:45',
          systolic: '124',
          dystolic: '83.5',
          pulse: '61.5'
        },
        {
          date: '2017/12/01',
          time: '07:45',
          systolic: '132',
          dystolic: '88',
          pulse: '62'
        },
        {
          date: '2017/12/02',
          time: '07:45',
          systolic: '129.5',
          dystolic: '80.5',
          pulse: '63.5'
        },
        {
          date: '2017/12/03',
          time: '07:45',
          systolic: '127.5',
          dystolic: '81.5',
          pulse: '71.5'
        },
        {
          date: '2017/12/04',
          time: '07:45',
          systolic: '138',
          dystolic: '88',
          pulse: '70.5'
        },
        {
          date: '2017/12/05',
          time: '07:45',
          systolic: '128',
          dystolic: '87',
          pulse: '68'
        },
        {
          date: '2017/12/06',
          time: '07:45',
          systolic: '138',
          dystolic: '81.5',
          pulse: '70'
        },
        {
          date: '2017/12/07',
          time: '07:45',
          systolic: '138',
          dystolic: '85',
          pulse: '65.5'
        },
        {
          date: '2017/12/08',
          time: '07:45',
          systolic: '124',
          dystolic: '83.5',
          pulse: '61.5'
        },
        {
          date: '2017/12/05',
          time: '07:45',
          systolic: '128',
          dystolic: '87',
          pulse: '68'
        },
        {
          date: '2017/12/06',
          time: '07:45',
          systolic: '138',
          dystolic: '81.5',
          pulse: '70'
        },
        {
          date: '2017/12/07',
          time: '07:45',
          systolic: '138',
          dystolic: '85',
          pulse: '65.5'
        },
        {
          date: '2017/12/08',
          time: '07:45',
          systolic: '124',
          dystolic: '83.5',
          pulse: '61.5'
        },
        {
          date: '2017/12/05',
          time: '07:45',
          systolic: '128',
          dystolic: '87',
          pulse: '68'
        },
        {
          date: '2017/12/06',
          time: '07:45',
          systolic: '138',
          dystolic: '81.5',
          pulse: '70'
        },
        {
          date: '2017/12/07',
          time: '07:45',
          systolic: '138',
          dystolic: '85',
          pulse: '65.5'
        },
        {
          date: '2017/12/08',
          time: '07:45',
          systolic: '124',
          dystolic: '83.5',
          pulse: '61.5'
        },
        {
          date: '2017/12/09',
          time: '07:45',
          systolic: '129.5',
          dystolic: '84',
          pulse: '69'
        }
      ]
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
    const xAxis = []
    const systolicVals = []
    const dystolicVals = []
    const pulseVals = []

    for (let reading of this.heartData) {
      xAxis.push(`${reading.date} ${reading.time}`)
      systolicVals.push(reading.systolic)
      dystolicVals.push(reading.dystolic)
      pulseVals.push(reading.pulse)
    }

    const options = {
      data: {
        x: 'x',
        xFormat: '%Y/%m/%d %H:%M',
        columns: [
          ['x', ...xAxis],
          ['Systolic', ...systolicVals],
          ['Dystolic', ...dystolicVals],
          ['Pulse', ...pulseVals]
        ]
      },
      axis: {
        x: {
          type: 'timeseries',
          tick: {
            format: '%Y/%m/%d %H:%M',
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
  max-height: 40vh;
}
.blood-pressure__data-view--table {
  overflow-y: scroll;
  overflow-x: hidden;
}
</style>

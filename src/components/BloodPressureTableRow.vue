<template>
  <tr>
    <td>{{ formatDate() }}</td>
    <td>{{ formatTime() }}</td>
    <td class="number-row">{{ heartDataRow.systolic }}</td>
    <td class="number-row">{{ heartDataRow.diastolic }}</td>
    <td class="number-row">{{ heartDataRow.pulse }}</td>
  </tr>
</template>

<script>
import moment from 'moment'

export default {
  name: 'BloodPressureTableRow',
  props: {
    heartDataRow: {
      type: Object
    }
  },
  data () {
    return {}
  },
  methods: {
    formatDate () {
      return moment(this.heartDataRow.date).format('ddd, MMM DD')
    },
    formatTime () {
      return moment(this.heartDataRow.time, 'h:mm A').format('h:mm A')
    }
  }
}
</script>

<style>

</style>

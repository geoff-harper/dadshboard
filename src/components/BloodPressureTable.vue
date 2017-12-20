<template>
  <table class="blood-pressure__table">
    <thead>
      <tr>
        <th>Date</th>
        <th>Time</th>
        <th class="number-row">Systolic</th>
        <th class="number-row">Diastolic</th>
        <th class="number-row">Pulse</th>
      </tr>
    </thead>
    <tbody>
      <BloodPressureTableRow v-for="(row, i) in heartData" :key="i" :heartDataRow="row"></BloodPressureTableRow>
    </tbody>
  </table>
</template>

<script>
import BloodPressureTableRow from './BloodPressureTableRow'

export default {
  name: 'BloodPressureTable',
  props: {
    heartData: {}
  },
  components: {
    BloodPressureTableRow
  },
  data () {
    return {}
  },
  methods: {}
}
</script>

<style lang="scss">
.blood-pressure__table {
  
}
</style>

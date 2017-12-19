<template>
  <tr>
    <td>{{ heartDataRow.date }}</td>
    <td>{{ heartDataRow.time }}</td>
    <td>{{ heartDataRow.systolic }}</td>
    <td>{{ heartDataRow.dystolic }}</td>
    <td>{{ heartDataRow.pulse }}</td>
  </tr>
</template>

<script>
export default {
  name: 'BloodPressureTableRow',
  props: {
    heartDataRow: {
      type: Object
    }
  },
  data () {
    return {}
  }
}
</script>

<style>

</style>

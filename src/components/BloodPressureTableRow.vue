<template>
  <tr>
    <td>ayy</td>
    <td>lmao</td>
    <td>{{ heartDatum.systolicVals }}</td>
    <td>{{ heartDatum.dystolicVals }}</td>
    <td>{{ heartDatum.pulseVals }}</td>
  </tr>
</template>

<script>
export default {
  name: 'BloodPressureTableRow',
  props: {
    heartDatum: {
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

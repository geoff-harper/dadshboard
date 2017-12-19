<template>
  <form @submit.prevent="" :class="['blood-pressure-form', hasError ? 'error' : '']">
      <input
        v-model="newDateText"
        class="blood-pressure-form__field"
        type="text"
        placeholder=" ">
      <input
        v-model="newTimeText"
        class="blood-pressure-form__field"
        type="text"
        placeholder=" ">
      <input
        v-model.number="newSystolicText"
        @click="newSystolicText = ''"
        class="blood-pressure-form__field"
        type="text"
        placeholder=" ">
      <input
        v-model.number="newDystolicText"
        @click="newDystolicText = ''"
        class="blood-pressure-form__field"
        type="text"
        placeholder=" ">
      <input
        v-model.number="newPulseText"
        @click="newPulseText = ''"
        class="blood-pressure-form__field"
        type="text"
        placeholder=" ">
    <button @click="emitReading" class="reading-add">&plus;</button>
  </form>
</template>

<script>
import moment from 'moment'

export default {
  name: 'BloodPressureInput',
  data () {
    return {
      newDateText: this.setDate(),
      newTimeText: this.setTime(),
      newSystolicText: 0,
      newDystolicText: 0,
      newPulseText: 0,
      hasError: false
    }
  },
  methods: {
    emitReading () {
      // console.log(moment(this.newDateText).isValid())
      // console.log(moment(this.newTimeText, 'h:mm A').isValid())
      let reading = {
        date: moment(this.newDateText).format('YYYY-MM-DD'),
        time: moment(this.newTimeText, 'h:mm A').format('h:mm A'),
        systolic: this.newSystolicText.toFixed(2),
        dystolic: this.newDystolicText.toFixed(2),
        pulse: this.newPulseText.toFixed(2)
      }

      this.$emit('add', reading)
    },
    setDate () {
      return moment().format('YYYY-MM-DD')
    },
    setTime () {
      return moment().format('h:mm A')
    }
  }
}
</script>

<style>

</style>

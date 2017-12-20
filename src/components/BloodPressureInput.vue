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
        @click="newSystolicText = null"
        class="blood-pressure-form__field"
        type="text"
        placeholder=" ">
      <input
        v-model.number="newDystolicText"
        @click="newDystolicText = null"
        class="blood-pressure-form__field"
        type="text"
        placeholder=" ">
      <input
        v-model.number="newPulseText"
        @click="newPulseText = null"
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
      newSystolicText: null,
      newDystolicText: null,
      newPulseText: null,
      hasError: false
    }
  },
  methods: {
    emitReading () {
      if (this.newSystolicText && this.newDystolicText && this.newPulseText !== null) {
        let reading = {
          date: moment(this.newDateText).format('YYYY-MM-DD'),
          time: moment(this.newTimeText, 'h:mm A').format('H:mm'),
          systolic: this.newSystolicText.toFixed(1),
          dystolic: this.newDystolicText.toFixed(1),
          pulse: this.newPulseText.toFixed(1)
        }
        this.$emit('add', reading)
      }
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

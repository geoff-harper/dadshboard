<template>
  <form @submit.prevent="" :class="['blood-pressure-form', hasError ? 'error' : '']">
      <input
        v-model="newDateText"
        class="blood-pressure-form__field"
        type="text"
        placeholder="">
      <input
        v-model="newTimeText"
        class="blood-pressure-form__field"
        type="text"
        placeholder="">
      <input
        v-model.number="newSystolicText"
        @click="newSystolicText = ''"
        class="blood-pressure-form__field"
        type="text"
        placeholder="">
      <input
        v-model.number="newDystolicText"
        @click="newDystolicText = ''"
        class="blood-pressure-form__field"
        type="text"
        placeholder="">
      <input
        v-model.number="newPulseText"
        @click="newPulseText = ''"
        class="blood-pressure-form__field"
        type="text"
        placeholder="">
    <button @click="emitReading" class="reading-add">&plus;</button>
  </form>
</template>

<script>
export default {
  name: 'BloodPressureInput',
  data () {
    return {
      newDateText: this.setDate(),
      newTimeText: this.setTime(),
      newSystolicText: '',
      newDystolicText: '',
      newPulseText: '',
      hasError: false
    }
  },
  methods: {
    emitReading () {
      console.log(this.newDateText)
      console.log(this.newTimeText)
      console.log(this.newSystolicText)
      console.log(this.newDystolicText)
      console.log(this.newPulseText)
    },
    setDate () {
      const today = new Date()
      const options = { year: 'numeric', month: '2-digit', day: '2-digit' }
      return `${today.toLocaleDateString('zh-Hans-CN', options)}`
    },
    setTime () {
      const now = new Date()
      const options = { hour: '2-digit', minute: '2-digit' }
      return `${now.toLocaleTimeString('en-US', options)}`
    }
  }
}
</script>

<style>

</style>

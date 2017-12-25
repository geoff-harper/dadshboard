<template>
  <form @submit.prevent="" :class="['blood-pressure-form', hasError ? 'error' : '']">
    <label class="blood-pressure-form__field-container field-container">
      Date
      <input
        v-model="newDateText"
        class="blood-pressure-form__field field"
        type="text"
        placeholder=" ">
    </label>
    <label class="blood-pressure-form__field-container field-container">
      Time
      <input
        v-model="newTimeText"
        class="blood-pressure-form__field field"
        type="text"
        placeholder=" ">
    </label>
    <label class="blood-pressure-form__field-container field-container">
      Systolic
      <input
        v-model.number="newSystolicText"
        @click="newSystolicText = null"
        class="blood-pressure-form__field field"
        type="text"
        placeholder=" ">
    </label>
    <label class="blood-pressure-form__field-container field-container">
      Diastolic
      <input
        v-model.number="newDiastolicText"
        @click="newDiastolicText = null"
        class="blood-pressure-form__field field"
        type="text"
        placeholder=" ">
    </label>
    <label class="blood-pressure-form__field-container field-container">
      Pulse
      <input
        v-model.number="newPulseText"
        @click="newPulseText = null"
        class="blood-pressure-form__field field"
        type="text"
        placeholder=" ">
    </label>
    <button @click="emitReading" class="blood-pressure-form__button button">&plus;</button>
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
      newDiastolicText: null,
      newPulseText: null,
      hasError: false
    }
  },
  methods: {
    emitReading () {
      if (this.newSystolicText && this.newDiastolicText && this.newPulseText !== null) {
        let reading = {
          date: moment(this.newDateText).format('YYYY-MM-DD'),
          time: moment(this.newTimeText, 'h:mm A').format('H:mm'),
          systolic: this.newSystolicText.toFixed(1),
          diastolic: this.newDiastolicText.toFixed(1),
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

<style lang="scss">
@import '~vars';
@import '~mixins';

  .blood-pressure-form {
    padding-top: 20px;
    
    .field {
      margin-bottom: 10px;
    }
  }
  
  @include bp(md) {
    .blood-pressure-form {
      display: flex;
      flex-flow: row nowrap;
      align-items: stretch;

      &__field-container {
        flex: 0 0 19%;
        
        .field {
          margin-bottom: 0px;
        }
      }
    }
  }
</style>

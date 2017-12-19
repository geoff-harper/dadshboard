<template>
  <div class="input-container">
    <input
      v-model="newReminderText"
      @keyup.enter="emitReminder"
      @click="newReminderText = '', hasError = false"
      :class="['reminder-input', hasError ? 'error' : '']"
      type="text"
      placeholder="">
    <button @click="emitReminder" class="reminder-add">&plus;</button>
  </div>
</template>

<script>
export default {
  name: 'ReminderInput',
  data () {
    return {
      newReminderText: '',
      hasError: false
    }
  },
  methods: {
    emitReminder () {
      if (this.newReminderText === '') {
        this.newReminderText = 'Please add text to reminder field.'
        this.hasError = true
      } else {
        this.hasError = false
        this.$emit('add', this.newReminderText)
        this.newReminderText = ''
      }
    }
  }
}
</script>

<style>

</style>

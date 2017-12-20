<template>
  <form @submit.prevent="" class="reminder-form">
    <label class="field-container">
      Add Reminder
      <input
        v-model="newReminderText"
        @keyup.enter="emitReminder"
        @click="newReminderText = '', hasError = false"
        :class="['reminder__field field', hasError ? 'error' : '']"
        type="text"
        placeholder="">
    </label>
    <button @click="emitReminder" class="reminder-add">&plus;</button>
  </form>
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

<style lang="scss">
.reminder-form {
  display: flex;
  flex-flow: row nowrap;

  .field-container {
    flex: 1 0 auto;
  }
}
</style>

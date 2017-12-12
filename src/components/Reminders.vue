<template>
  <section id="reminders" class="card card--small-view">
    <ReminderInput @add="addReminder"></ReminderInput>
    <ul>
      <ReminderItem
        v-for="(reminder, i) in allReminders"
        :key="reminder.id"
        :reminder="reminder"
        @delete="deleteReminder"></ReminderItem>
    </ul>
  </section>
</template>

<script>
import ReminderItem from './ReminderItem'
import ReminderInput from './ReminderInput'

let currentReminderId = 0

export default {
  components: {
    ReminderItem,
    ReminderInput
  },
  methods: {
    addReminder (reminderToAdd) {
      this.allReminders.push({
        text: reminderToAdd,
        checked: false,
        id: ++currentReminderId
      })
    },
    deleteReminder (idToRemove) {
      this.allReminders = this.allReminders.filter(reminder => {
        return reminder.id !== idToRemove
      })
    }
  },
  data () {
    return {
      allReminders: [
        {
          text: 'Make a to-do list knockoff with the Vue.js framework',
          id: ++currentReminderId
        }
      ]
    }
  }
}
</script>

<style>

</style>

<template>
  <section id="reminders" class="card card--small-view">
    <h1 class="card__title">Reminders</h1>
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
  name: 'Reminders',
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
          text: 'Water Christmas tree',
          id: ++currentReminderId
        }
      ]
    }
  }
}
</script>

<style>

</style>

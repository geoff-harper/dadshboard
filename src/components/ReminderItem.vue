<template>
  <li class="reminder-item">
    <p>{{ reminder.text }}</p>
    <button @click.stop="$emit('delete', reminder.id)" class="button">&times;</button>
  </li>
</template>

<script>
export default {
  name: 'ReminderItem',
  props: {
    reminder: {
      type: Object,
      required: true
    }
  },
  data () {
    return {

    }
  }
}
</script>

<style lang="scss">
@import '~vars';
  
.reminder-item {
  display: flex;
  flex-flow: row nowrap;
  justify-content: space-between;
  align-items: flex-start;
  border-bottom: 1px solid $border-colour;
  padding: 10px 0;
  
  p {
    padding: 0 10px 0 0;
    margin: 0;
  }
  
  &:last-child {
    border: none;
  }
}
</style>

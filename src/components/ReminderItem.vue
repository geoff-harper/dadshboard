<template>
  <li class="reminder-item">
    <p>{{ reminder.text }}</p>
    <button @click.stop="$emit('delete', reminder.id)">&times;</button>
  </li>
</template>

<script>
export default {
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

<style>

</style>

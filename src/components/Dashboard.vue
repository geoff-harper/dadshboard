<template>
  <main class="card-container">
    <Reminders></Reminders>
    <Weather></Weather>
    <BlueJays></BlueJays>
    <FreezerStock></FreezerStock>
  </main>
</template>

<script>
import Reminders from './Reminders'
import BlueJays from './BlueJays'
import Weather from './Weather'
import FreezerStock from './FreezerStock'

export default {
  name: 'Dashboard',
  components: {
    Reminders,
    BlueJays,
    Weather,
    FreezerStock
  },
  data () {
    return {

    }
  }
}
</script>

<style>
.card-container {
  padding: 20px;
  display: grid;
  grid-template-rows: 1fr 1fr;
  grid-template-columns: 1fr 1fr 1fr;
  grid-gap: 20px;
}
.card {
  padding: 20px;
  border: 1px solid #EEE;
}
</style>

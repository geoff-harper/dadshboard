<template>
  <main class="card-container">
    <Reminders></Reminders>
    <Weather></Weather>
    <BlueJays></BlueJays>
    <FreezerStock></FreezerStock>
    <BloodPressure></BloodPressure>
  </main>
</template>

<script>
import Reminders from './Reminders'
import BlueJays from './BlueJays'
import Weather from './Weather'
import FreezerStock from './FreezerStock'
import BloodPressure from './BloodPressure'

import 'normalize.css'
import '../sass/main.scss'

export default {
  name: 'Dashboard',
  components: {
    Reminders,
    BlueJays,
    Weather,
    FreezerStock,
    BloodPressure
  },
  data () {
    return {

    }
  }
}
</script>

<style lang="scss">
.card-container {
  padding: 20px;
  height: 100vh;
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

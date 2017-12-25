<template>
  <main class="card-container">
    <BloodPressure></BloodPressure>
    <Reminders></Reminders>
    <FreezerStock></FreezerStock>
    <Weather></Weather>
    <BlueJays></BlueJays>   
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

</style>

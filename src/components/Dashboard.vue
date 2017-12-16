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

<style>
html {
  font-family: sans-serif;
}
* {
  box-sizing: border-box;
}
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
#blood-pressure.card {
  grid-column: 1 / span 2;
  grid-row: 1 / 2;
}
figure {
  margin: 0;
}
ul {
  list-style: none;
  padding: 0;
}
</style>

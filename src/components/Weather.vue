<template>
  <section id="weather" class="card card--small-view">
    <img :src="weather.icon_url" :alt="weather.icon" class="weather__icon">
    <h2 class="weather__condition">{{ weather.conditions }}</h2>
    <figure class="weather__temp">{{ weather.high.celsius }} / {{ weather.low.celsius }}</figure>
  </section>
</template>

<script>
// http://api.wunderground.com/api/f749d373cd615180/geolookup/q/Canada/Gananoque.json

export default {
  name: 'Weather',
  data () {
    return {
      weather: {
        icon_url: '',
        icon: '',
        conditions: '',
        high: { celsius: '' },
        low: { celsius: '' }
      }
    }
  },
  methods: {
    getWeather () {
      fetch('http://api.wunderground.com/api/f749d373cd615180/forecast/q/Canada/Gananoque.json')
        .then(async res => {
          const data = await res.json()
          this.weather = data.forecast.simpleforecast.forecastday[0]
        })
        .catch(err => { console.log(err) })
    }
  },
  mounted () {
    this.getWeather()
  }
}
</script>

<style>

</style>

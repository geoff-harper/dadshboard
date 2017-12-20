<template>
  <section id="weather" class="card card--small-view">
    <h1 class="card__title">Weather</h1>
    <img :src="weather.icon_url" :alt="weather.icon" class="weather__icon">
    <h2 class="weather__condition">{{ weather.conditions }}</h2>
    <p class="weather__temp">{{ weather.high.fahrenheit }}&#8457; / {{ weather.low.fahrenheit }}&#8457;</p>
    <div class="weather__other">
      <div class="weather__pop">
        <h3 class="weather__small-title">Precipitation</h3>
        {{ weather.pop }}%
      </div>
      <div class="weather__humidity">
        <h3 class="weather__small-title">Humidity</h3>
        {{ weather.avehumidity }}%
      </div>
      <div class="weather__wind">
        <h3 class="weather__small-title">Wind Conditions</h3>
        {{ weather.avewind.mph }}m/h {{ weather.avewind.dir }}
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'Weather',
  data () {
    return {
      weather: {
        icon_url: '',
        icon: '',
        conditions: '',
        high: { fahrenheit: '' },
        low: { fahrenheit: '' },
        pop: '',
        avehumidity: '',
        avewind: {
          dir: '',
          mph: ''
        }
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
        .then(() => {
          this.weather.avewind.dir = this.weather.avewind.dir.slice(1)
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

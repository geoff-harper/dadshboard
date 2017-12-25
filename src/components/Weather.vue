<template>
  <section id="weather" class="card card--small-view">
    <h1 class="card__title">Weather</h1>  
    <div class="weather__main">
      <img :src="weather.icon_url" :alt="weather.icon" class="weather__icon">
      <h2 class="weather__condition subtitle">{{ weather.conditions }}</h2>    
    </div>   
    <p class="weather__temp">{{ weather.high.fahrenheit }}&deg;F / {{ weather.low.fahrenheit }}&deg;F</p>
    <div class="weather__pop">
      <h3 class="weather__small-title small-subtitle">Precipitation</h3>
      <p class="small-data">{{ weather.pop }}%</p>
    </div>
    <div class="weather__humidity">
      <h3 class="weather__small-title small-subtitle">Humidity</h3>
      <p class="small-data">{{ weather.avehumidity }}%</p>
    </div>
    <div class="weather__wind">
      <h3 class="weather__small-title small-subtitle">Wind Conditions</h3>
      <p class="small-data">{{ weather.avewind.mph }}m/h {{ weather.avewind.dir }}</p>
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

<style lang="scss"> 
@import '~mixins';

.weather__temp {
  font-size: 42px;
  line-height: 1em;
  text-align: center;
  align-self: center;
  margin-bottom: 20px;
}
  
.weather__icon {
  display: block;
  margin: 0 auto;
}

.weather__condition {
  text-align: center;
}
  
  .weather__pop,
  .weather__humidity,
  .weather__wind {
  margin-bottom: 20px;
  text-align: center;
}
  
@include bp(md) {
  .weather__temp {
    text-align: right;
    margin-bottom: 0px;
  }
  
  .weather__icon {
    margin: 0;
  }

  .weather__condition {
    text-align: left;
  }
  
  .weather__pop,
  .weather__humidity,
  .weather__wind {
    margin-top: 0;
    text-align: left;
  }
}
</style>

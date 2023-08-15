<template>
  <q-page class="flex column">
    <div class="col q-pt-lg q-px-md">
      <q-input v-model="search" placeholder="search" dark
      borderless>

        <template v-slot:before>
          <q-icon  name="my_location" @click="getLocation"/>
        </template>

        <template v-slot:append>
          <q-btn round dense flat icon="search" />
        </template>
      </q-input>

    </div>

  <template v-if="weatherData">
    <div class="col text-white text-center">
      <div class="text-h4 text-weight-light">
        Uganda
      </div>
      <div class="text-h6 text-weight-light">
        Cloudy
      </div>
      <div class="text-h4 text-weight-thin">

        8&deg;
      </div>

    </div>
  </template>
  <template v-else>
    <div class="col column text-center text-white">
      <div  class="col text-h2 text-weight-thin">

        Quasar<br>Weather
      </div>

    </div>

    <q-btn class="col" flat>
      <q-icon left size="3em" @click="getLocation" name="my_location" />
      <div>find my location</div>
    </q-btn>

  </template>

<div class="col text-center">
  <img src="https://www.fillmurray.com/100/100" alt="Bill">
</div>

<div class="col skyline">

</div>
  </q-page>
</template>

<script>
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'IndexPage',
  data () {
    return {
      search: '',
      weatherData: null,
      lat: null,
      lan: null,
      apiUrl: 'https://api.openweathermap.org/data/2.5/weather',
      apiKey: '119fda3067abfbc82838148e3132f3ec'
    }
  },
  methods: {
    getLocation () {
      navigator.geolocation.getCurrentPosition(position => {
        console.log('position:', position)
        /* this.lat = position.coords.latitude
        this.lon = position.cooords.longitude
        this.getWeatherByCoords() */
      }

      )
    }
    /* getWeatherByCoords () {
      this.$axios(`${this.apiUrl}?lat=${this.lat}&lon=${this.lon}&appid=${this.apiKey}&units=metric`).then(response => {
        this.weatherData= response)
      })
    } */

  }
})
</script>

<style lang="sass">
.q-page
  background: linear-gradient(to bottom,#136a8a, #267871)
.skyline
  flex: 0 0 100px
  background:url(../static/skyline.png)
  background-size:contain
  background-position:center bottom
</style>

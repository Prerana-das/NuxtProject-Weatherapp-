
<template>
  <v-container>

    <h1 class="display-1 text-xs-center app_title">Weather App</h1>
    <v-flex xs12>
      <v-card color="cyan darken-4" dark>
        <v-card-text>
          <v-layout justify-center>
            <!-- One -->
            <v-flex v-if="weather.weather" xs4 class="text-xs-center">
              <h4>Temperature</h4>
              <h1 class="display-1">{{ weather.name }}</h1>
              <img :src="icon" alt="weather icon" />
              <p>
                <span class="display-1">{{ temp() }} &deg;C</span>
                <span class="caption ml-4">{{
                  weather.weather[0].description
                }}</span>
              </p>
            </v-flex>

            <!-- Two -->
             <v-flex v-if="weather.weather" xs4 class="text-xs-center">
                <h4>Wind & Pressure::</h4>
                <h3 class="headline mt-4">
                     Gust:
                    {{ weather.wind.gust }}
                </h3>
                <h3 class="headline mt-4">
                    Speed:
                    {{ weather.wind.speed }}
                </h3>
            </v-flex>


             <!-- Three -->
             <v-flex v-if="weather.weather" xs4 class="text-xs-center">
                <h4>Other:</h4>
                <h3 class="headline mt-4">
                    Max Temperature:
                    {{ Math.round(weather.main.temp_max - 273) }} &deg; C
                </h3>
                <h3 class="headline mt-4">
                    Min Temperature:
                    {{ Math.round(weather.main.temp_min - 273) }} &deg; C
                </h3>
            </v-flex>
        
          </v-layout>
        </v-card-text>
      </v-card>
    </v-flex>
    <v-flex xs12 class="mt-4">
      <v-form @submit.prevent="getWeatherInfo">
        <v-text-field
          v-model="city"
          label="Enter city name"
          solo
        ></v-text-field>
      </v-form>
    </v-flex>
    
  </v-container>
</template>

<script>
export default {
  data() {
    return {
      city: 'London',
    //   weather:{}
    }
  },
  computed: {
    icon() {
      return this.weather.weather
        ? `https://openweathermap.org/img/w/${this.weather.weather[0].icon}.png`
        : ''
    }
  },
  asyncData({ params, $axios }) {
    return $axios
      .$get(
        `https://api.openweathermap.org/data/2.5/weather?q=London&appid=55f6714f97e6bdc9b999c5a412736ada`
      )
      .then(res => {
        return { weather: res }
      })
  },
  methods: {
    getWeatherInfo() {
        
      this.$axios
        .$get(
          `https://api.openweathermap.org/data/2.5/weather?q=${
            this.city
          }&appid=55f6714f97e6bdc9b999c5a412736ada`
        )
        .then(res => (this.weather = res))
    },
    temp() {
      return this.weather.main ? Math.round(this.weather.main.temp - 273) : ''
    }
  }
}
</script>

<style>

.app_title {
    margin-bottom: 30px;
    margin-top: 20px;
    text-align: center;
    text-transform: uppercase;
    font-size: 25px!important;
}


</style>
<template>
  <div class="home flex-grow-1 d-flex flex-column">
    <div>
      <div class="row justify-content-center">
        <h2>CURRENT</h2>
      </div>
      <div class="row mt-5 justify-content-around">
        <div class="col-6 card" v-if="state.weather.current">
          <div class="">
            <h3>{{ state.weather.timezone }}</h3>
            <h3>{{ state.weather.current.weather[0].main }}</h3>
            <img
              v-if="state.weather.current.weather[0].main == 'Clear'"
              src="../assets/img/01d.png"
              alt=""
            />
          </div>
          <h6>Feels Like: {{ state.weather.current.feels_like }}&#176; F</h6>
          <h6>Humidity: {{ state.weather.current.humidity }}%</h6>
          <h6>Cloud Coverage: {{ state.weather.current.clouds }}%</h6>
          <h6>UV Index: {{ state.weather.current.uvi }}</h6>
        </div>
      </div>
    </div>
    <div class="row justify-content-center text-center mt-5">
      <div><h1>Weekly Forecast</h1></div>
    </div>
    <div
      class="row mt-5 justify-content-around text-center"
      v-if="state.weather.daily"
    >
      <div class="col-2 card">
        <h4>{{ state.weather.daily[0].weather[0].main }}</h4>
        <h6>Morning: {{ state.weather.daily[0].feels_like.morn }}&#176; F</h6>
        <h6>Afternoon: {{ state.weather.daily[0].feels_like.day }}&#176; F</h6>
        <h6>Evening: {{ state.weather.daily[0].feels_like.eve }}&#176; F</h6>
        <h6>Night: {{ state.weather.daily[0].feels_like.night }}&#176; F</h6>
      </div>
      <div class="col-2 card">
        <h4>{{ state.weather.daily[1].weather[0].main }}</h4>
        <h6>Morning: {{ state.weather.daily[1].feels_like.morn }}&#176; F</h6>
        <h6>Afternoon: {{ state.weather.daily[1].feels_like.day }}&#176; F</h6>
        <h6>Evening: {{ state.weather.daily[1].feels_like.eve }}&#176; F</h6>
        <h6>Night: {{ state.weather.daily[1].feels_like.night }}&#176; F</h6>
      </div>
      <div class="col-2 card">
        <h4>{{ state.weather.daily[2].weather[0].main }}</h4>
        <h6>Morning: {{ state.weather.daily[2].feels_like.morn }}&#176; F</h6>
        <h6>Afternoon: {{ state.weather.daily[2].feels_like.day }}&#176; F</h6>
        <h6>Evening: {{ state.weather.daily[2].feels_like.eve }}&#176; F</h6>
        <h6>Night: {{ state.weather.daily[2].feels_like.night }}&#176; F</h6>
      </div>
      <div class="col-2 card">
        <h4>{{ state.weather.daily[3].weather[0].main }}</h4>
        <h6>Morning: {{ state.weather.daily[3].feels_like.morn }}&#176; F</h6>
        <h6>Afternoon: {{ state.weather.daily[3].feels_like.day }}&#176; F</h6>
        <h6>Evening: {{ state.weather.daily[3].feels_like.eve }}&#176; F</h6>
        <h6>Night: {{ state.weather.daily[3].feels_like.night }}&#176; F</h6>
      </div>
      <div class="col-2 card">
        <h4>{{ state.weather.daily[4].weather[0].main }}</h4>
        <h6>Morning: {{ state.weather.daily[4].feels_like.morn }}&#176; F</h6>
        <h6>Afternoon: {{ state.weather.daily[4].feels_like.day }}&#176; F</h6>
        <h6>Evening: {{ state.weather.daily[4].feels_like.eve }}&#176; F</h6>
        <h6>Night: {{ state.weather.daily[4].feels_like.night }}&#176; F</h6>
      </div>
    </div>
  </div>
</template>

<script>
import { computed, onMounted, reactive } from 'vue'
import { weatherService } from '../services/WeatherService'
import { useRoute } from 'vue-router'
import { AppState } from '../AppState'
export default {
  name: 'Home',
  setup() {
    // const { icon } = data.weather[0]
    // locationIcon = document.querySelector('.weather-icon')
    // locationIcon.innerHTML = `<img src="icons/${icon}.png">`
    const route = useRoute()
    const state = reactive({
      weather: computed(() => AppState.weather)
    })
    onMounted(async () => {
      await weatherService.getWeather(route.params.current)
    })
    return {
      state,
      route
    }
  }
}
</script>

<style scoped lang="scss">
.home {
  text-align: center;
  user-select: none;
  > img {
    height: 200px;
    width: 200px;
  }
}
</style>

<template>
  <div class="home flex-grow-1 d-flex flex-column">
    <div>
      <div class="row mt-5">
        <div class="col-4 card" v-if="state.weather.current">
          <div class="">
            <h2>CURRENT</h2>
            <h3>{{ state.weather.timezone }}</h3>
            <h3>{{ state.weather.current.weather[0].icon }}</h3>
            <h6>Feels Like: {{ state.weather.current.feels_like }}</h6>
            <h6>Humidity: {{ state.weather.current.humidity }}%</h6>
            <h6>Cloud Coverage: {{ state.weather.current.clouds }}%</h6>
            <h6>UV Index: {{ state.weather.current.uvi }}</h6>
          </div>
        </div>
        <div class="col-2"></div>
        <div class="col-2"></div>
        <div class="col-2"></div>
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
  props: {
    weather: { type: Object, required: true }
  },
  setup() {
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

<template>
  <div
    class="home flex-grow-1 d-flex flex-column align-items-center justify-content-center"
  ></div>
  <div>
    <div class="row">
      <div class="col-2">
        <h6>{{ state }}</h6>
      </div>
      <div class="col-2"></div>
      <div class="col-2"></div>
      <div class="col-2"></div>
      <div class="col-2"></div>
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

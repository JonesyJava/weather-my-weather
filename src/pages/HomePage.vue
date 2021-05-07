<template>
  <div
    class="home flex-grow-1 d-flex flex-column align-items-center justify-content-center"
  ></div>
</template>

<script>
import { onMounted } from 'vue'
import { weatherService } from '../services/WeatherService'
export default {
  name: 'Home',
  setup() {
    onMounted(async () => {
      await weatherService.getWeather()
    })
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

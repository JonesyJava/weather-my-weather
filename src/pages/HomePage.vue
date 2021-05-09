<template>
  <div class="home flex-grow-1 d-flex flex-column container-fluid bg">
    <div class="wrap">
      <div class="row justify-content-center mt-3">
        <h1 class="wthr-font text-white">CURRENT</h1>
      </div>
      <div class="row mt-3 justify-content-around">
        <div
          class="col-md-2 col-sm-4 card text-white"
          v-if="state.weather.current"
        >
          <h3 class="wthr-font">
            {{ state.weather.timezone }}
          </h3>
          <h3>{{ state.weather.current.weather[0].main }}</h3>
          <div>
            <img
              v-if="state.weather.current.weather[0].main == 'Clear'"
              src="../assets/img/01d.png"
              alt="Clear Image"
            />
            <img
              v-if="state.weather.current.weather[0].main == 'Clouds'"
              src="../assets/img/02d.png"
              alt="Cloudy Image"
            />
            <img
              v-if="state.weather.current.weather[0].main == 'Rain'"
              src="../assets/img/09d.png"
              alt="Rain Image"
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
      <div>
        <h2 class="wthr-font text-white">5-Day Forecast</h2>
      </div>
    </div>
    <div
      class="row my-3 justify-content-around text-center text-white"
      v-if="state.weather.daily"
    >
      <div class="col-md-2 col-sm-1 card">
        <h4>{{ state.weather.daily[0].weather[0].main }}</h4>
        <img
          v-if="state.weather.daily[0].weather[0].main == 'Clear'"
          src="../assets/img/01d.png"
          alt="Clear Image"
        />
        <img
          v-if="state.weather.daily[0].weather[0].main == 'Clouds'"
          src="../assets/img/02d.png"
          alt="Cloudy Image"
        />
        <img
          v-if="state.weather.daily[0].weather[0].main == 'Rain'"
          src="../assets/img/09d.png"
          alt="Rain Image"
        />
        <h6>Morning: {{ state.weather.daily[0].feels_like.morn }}&#176; F</h6>
        <h6>Afternoon: {{ state.weather.daily[0].feels_like.day }}&#176; F</h6>
        <h6>Evening: {{ state.weather.daily[0].feels_like.eve }}&#176; F</h6>
        <h6>Night: {{ state.weather.daily[0].feels_like.night }}&#176; F</h6>
      </div>
      <div class="col-md-2 col-sm-1 card">
        <h4>{{ state.weather.daily[1].weather[0].main }}</h4>
        <img
          v-if="state.weather.daily[1].weather[0].main == 'Clear'"
          src="../assets/img/01d.png"
          alt="Clear Image"
        />
        <img
          v-if="state.weather.daily[1].weather[0].main == 'Clouds'"
          src="../assets/img/02d.png"
          alt="Cloudy Image"
        />
        <img
          v-if="state.weather.daily[1].weather[0].main == 'Rain'"
          src="../assets/img/09d.png"
          alt="Rain Image"
        />
        <h6>Morning: {{ state.weather.daily[1].feels_like.morn }}&#176; F</h6>
        <h6>Afternoon: {{ state.weather.daily[1].feels_like.day }}&#176; F</h6>
        <h6>Evening: {{ state.weather.daily[1].feels_like.eve }}&#176; F</h6>
        <h6>Night: {{ state.weather.daily[1].feels_like.night }}&#176; F</h6>
      </div>
      <div class="col-md-2 col-sm-1 card">
        <h4>{{ state.weather.daily[2].weather[0].main }}</h4>
        <img
          v-if="state.weather.daily[2].weather[0].main == 'Clear'"
          src="../assets/img/01d.png"
          alt="Clear Image"
        />
        <img
          v-if="state.weather.daily[2].weather[0].main == 'Clouds'"
          src="../assets/img/02d.png"
          alt="Cloudy Image"
        />
        <img
          v-if="state.weather.daily[2].weather[0].main == 'Rain'"
          src="../assets/img/09d.png"
          alt="Rain Image"
        />
        <h6>Morning: {{ state.weather.daily[2].feels_like.morn }}&#176; F</h6>
        <h6>Afternoon: {{ state.weather.daily[2].feels_like.day }}&#176; F</h6>
        <h6>Evening: {{ state.weather.daily[2].feels_like.eve }}&#176; F</h6>
        <h6>Night: {{ state.weather.daily[2].feels_like.night }}&#176; F</h6>
      </div>
      <div class="col-md-2 col-sm-1 card">
        <h4>{{ state.weather.daily[3].weather[0].main }}</h4>
        <img
          v-if="state.weather.daily[3].weather[0].main == 'Clear'"
          src="../assets/img/01d.png"
          alt="Clear Image"
        />
        <img
          v-if="state.weather.daily[3].weather[0].main == 'Clouds'"
          src="../assets/img/02d.png"
          alt="Cloudy Image"
        />
        <img
          v-if="state.weather.daily[3].weather[0].main == 'Rain'"
          src="../assets/img/09d.png"
          alt="Rain Image"
        />
        <h6>Morning: {{ state.weather.daily[3].feels_like.morn }}&#176; F</h6>
        <h6>Afternoon: {{ state.weather.daily[3].feels_like.day }}&#176; F</h6>
        <h6>Evening: {{ state.weather.daily[3].feels_like.eve }}&#176; F</h6>
        <h6>Night: {{ state.weather.daily[3].feels_like.night }}&#176; F</h6>
      </div>
      <div class="col-md-2 col-sm-1 card">
        <h4>{{ state.weather.daily[4].weather[0].main }}</h4>
        <img
          v-if="state.weather.daily[4].weather[0].main == 'Clear'"
          src="../assets/img/01d.png"
          alt="Clear Image"
        />
        <img
          v-if="state.weather.daily[4].weather[0].main == 'Clouds'"
          src="../assets/img/02d.png"
          alt="Cloudy Image"
        />
        <img
          v-if="state.weather.daily[4].weather[0].main == 'Rain'"
          src="../assets/img/09d.png"
          alt="Rain Image"
        />
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
.wthr-font {
  font-family: "Cinzel", serif;
}
.bg {
  background-image: url("https://greatloveart.com/wp-content/uploads/2021/01/4k-Artistic-Nature-Background-Laptop-Wallpapers.jpg");
  background-position: center;
  background-size: cover;
}
.card {
  background-color: rgba(245, 245, 245, 0.192);
  -webkit-backdrop-filter: blur(10px) !important;
  border-radius: 10%;
}
@media screen {
  .card {
    margin-top: 15px;
    margin-right: 30px;
    margin-left: 30px;
  }
}
</style>

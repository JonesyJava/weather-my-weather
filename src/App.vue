<template>
  <header>
    <Navbar />
  </header>
  <main>
    <router-view />
  </main>
  <footer>
    <div class="bg text-light text-center p-2 wthr-font">
      Brought To You By
      <img
        src="https://raw.githubusercontent.com/bugsounet/MMM-Weather/master/logo.png"
        alt=""
        height="45"
      />
    </div>
  </footer>
</template>

<script>
import { computed } from 'vue'
import { AppState } from './AppState'
export default {
  name: 'App',
  setup() {
    return {
      appState: computed(() => AppState)
    }
  }
}
</script>
<style lang="scss">
@import "./assets/scss/main.scss";
.wthr-font {
  font-family: "Cinzel", serif;
}
.bg {
  background-color: rgba(144, 48, 235, 0.658);
}
</style>

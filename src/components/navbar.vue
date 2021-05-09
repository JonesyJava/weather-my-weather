<template>
  <nav class="navbar navbar-expand-lg navbar-light bg">
    <router-link class="navbar-brand d-flex" :to="{ name: 'Home' }">
      <div class="d-flex flex-column align-items-center">
        <img
          alt="logo"
          src="https://images-na.ssl-images-amazon.com/images/I/61nuuPxUvaL.png"
          height="45"
        />
      </div>
      <h4 class="ml-3 text-light wthr-font pt-2 nav-title">
        Weather The Weather
      </h4>
      <h6 class="ml-1 text-light">®</h6>
    </router-link>
  </nav>
</template>

<script>
import { AuthService } from '../services/AuthService'
import { AppState } from '../AppState'
import { computed, reactive } from 'vue'
export default {
  name: 'Navbar',
  setup() {
    const state = reactive({
      dropOpen: false
    })
    return {
      state,
      user: computed(() => AppState.user),
      async login() {
        AuthService.loginWithPopup()
      },
      async logout() {
        await AuthService.logout({ returnTo: window.location.origin })
      }
    }
  }
}
</script>

<style scoped>
.dropdown-menu {
  user-select: none;
  display: block;
  transform: scale(0);
  transition: all 0.15s linear;
}
.dropdown-menu.show {
  transform: scale(1);
}
.hoverable {
  cursor: pointer;
}
a:hover {
  text-decoration: none;
}
.nav-link {
  text-transform: uppercase;
}
.nav-item .nav-link.router-link-exact-active {
  color: var(--primary);
}
.bg {
  background-color: rgba(144, 48, 235, 0.658);
}
.wthr-font {
  font-family: "Cinzel", serif;
}
@media screen {
  .nav-title {
    font-size: 21px;
  }
}
</style>

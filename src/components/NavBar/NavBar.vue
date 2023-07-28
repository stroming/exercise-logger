<script>
import NavBarLink from './NavBarLink.vue'
import FontAwesomeIcon from '../../App.vue'
import { collapsed, toggleNavbar, navbarWidth } from './state.js'

export default {
  props: {},
  components: { NavBarLink },
  setup() {
    return { collapsed, toggleNavbar, navbarWidth }
  }
}
</script>

<template>
  <div class="navbar" :style="{ width: navbarWidth }">
    <h1>
      <span v-if="collapsed">
        <div>V</div>
        <div>S</div>
      </span>
      <span v-else>
        <img alt="Vue logo" class="logo" src="@/assets/logo.svg" width="125" height="125" />
        <p>Vue Navbar</p>
      </span>
    </h1>

    <div class="links">
      <NavBarLink to="/log" icon="fa-solid fa-house fa-fw">Home</NavBarLink>
      <NavBarLink to="/log" icon="fa-solid fa-house">Home</NavBarLink>
      <NavBarLink to="/log" icon="fa-solid fa-house">Home</NavBarLink>
      <NavBarLink to="/log" icon="fa-solid fa-house">Home</NavBarLink>
      <NavBarLink to="/log" icon="fa-solid fa-house">Home</NavBarLink>
    </div>

    <span class="collapse-icon" :class="{ 'rotate-180': !collapsed }" @click="toggleNavbar">
      <font-awesome-icon :icon="['fas', 'arrow-up-right-from-square']" />
    </span>

  </div>
</template>

<style>
:root {
  --navbar-bg-color: #2f855a;
  --navbar-item-hover: #38a169;
  --navbar-item-active: #276749;
}
</style>


<style scoped>
.links {
  margin-top: 10em;
}

.navbar {
  color: white;
  background-color: var(--navbar-bg-color);

  float: left;
  position: fixed;
  z-index: 1;
  top: 0;
  left: 0;
  bottom: 0;
  padding: 0.8em;

  transition: 0.8s ease;

  display: flex;
  flex-direction: column;
}

.navbar h1 {
  height: 2.5em;
}

.navlink{
  height: 40%;
  margin: 0em;
}

.collapse-icon {
  position: absolute;
  bottom: 0;
  padding: 0.5em;

  color: rgba(255, 255, 255, 0.7);

  transition: 0.2s linear;
}

.rotate-180 {
  transform: rotate(180deg);
  transition: 0.2s linear;
}
</style>

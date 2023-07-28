<script>
import { computed } from 'vue'
import { useRoute } from 'vue-router'
import { collapsed } from './state.js'

export default {
  props: {
    to: { type: String, required: true },
    icon: { type: String, required: true }
  },
  setup(props) {
    const route = useRoute()
    const isActive = computed(() => route.path === props.to)
    return { isActive, collapsed }
  }
}
</script>

<template>
  <router-link :to="to" class="link" :class="{ active: isActive }">
    <font-awesome-icon :icon="icon" />
    <transition name="fade">
      <span v-if="!collapsed">
        <slot />
      </span>
    </transition>
  </router-link>
</template>

<style scoped>
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.1s;
}

.fade-enter,
.fade-leave-to {
  opacity: 0;
}

.link {
  display: flex;
  align-items: center;

  cursor: pointer;
  position: relative;
  font-weight: 400;
  user-select: none;


  margin: 1em -0.2em;
  padding: 0.4em;
  border-radius: 0.3em;
  height: 2em;

  color: white;
  text-decoration: none;
  text-indent: 0.5em;
}

.link:hover {
  background-color: var(--navbar-item-hover);
}

.link.active {
  background-color: var(--navbar-item-active);
}

.link .icon {
  flex-shrink: 0;
  width: 25px;
  margin-right: 10px;
}
</style>
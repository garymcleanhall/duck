<template>
  <transition-group name="build" tag="div" class="ui stackable cards">
    <Build v-for="build in builds" :key="build.id" :build="build" />
  </transition-group>
</template>

<script>
import Build from "./Build.vue";

export default {
  props: ["builds"],
  components: {
    Build
  }
};
</script>

<style scoped>
#app .build-enter-active,
#app .build-leave-active {
  transition: 1s cubic-bezier(0.59, 0.12, 0.34, 0.95);
  transition-property: opacity, transform;
}

#app .build-move {
  transition: transform 1s;
  transition-property: opacity, transform;
}

#app .build-enter {
  opacity: 0;
  transform: translateX(50px) scaleY(0.75);
}

#app .build-enter-to {
  opacity: 1;
  transform: translateX(0) scaleY(1);
}

#app .build-leave-active {
  position: absolute;
}

#app .build-leave-to {
  opacity: 0;
  transform: translateX(0);
  transform-origin: center top;
}
</style>
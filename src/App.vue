<template>
  <div>
    <transition
        enter-active-class="animate__animated animate__fadeInDown"
        leave-active-class="animate__animated animate__fadeOutUp"
        mode="out-in">
      <components
          :key="activeComponent"
          :is="activeComponent"
      ></components>
    </transition>
  </div>
</template>

<script>

import GameCards from "./components/GameCards";
import Congratulate from "./components/Congratulate";
import Fail from "./components/Fail";
import eventBus from "./eventBus";

export default {
  data: function () {
    return {
      activeComponent: "app-game-cards"
    }
  },
  components: {
    "app-game-cards": GameCards,
    "app-congratulate": Congratulate,
    "app-fail": Fail
  },
  created() {
    eventBus.$on('activeComponent', (component) => {
      setTimeout(() => {
        this.activeComponent = component;
      }, 3500);
    });
    eventBus.$on('restartGame', (component) => {
      this.activeComponent = component;
    });
  }
}
</script>

<style>
body {
  font-family: sans-serif;
}
</style>

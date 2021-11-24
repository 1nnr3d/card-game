<template>
  <div>
    <transition
        enter-active-class="animate__animated animate__rotateInDownLeft"
        leave-active-class="animate__animated animate__rotateOutDownLeft"
        mode="out-in">
      <div
          :key="'card'"
          @click="cardCheck"
          v-if="!showDefaultCard"
          class="card"></div>
      <div
          :key="'default-card'"
          :style="{backgroundImage: defaultCard}"
          v-if="showDefaultCard"
          class="default-card"></div>
    </transition>
  </div>
</template>

<script>
import eventBus from "../../eventBus";

export default {
  data: function (){
    return {
      defaultCard: `url('src/assets/card-${this.default}.jpg')`,
      showDefaultCard: false
    }
  },
  props: ["default", "selected"],
  methods: {
    cardCheck: function (){
      if(this.selected != null){
        this.showDefaultCard = true
        if(this.selected == this.default){
          eventBus.$emit('activeComponent', 'app-congratulate')
        } else {
          eventBus.$emit('activeComponent', 'app-fail')
        }
      } else {
        alert('Lütfen bir kart seçiniz!')
      }
    }
  }
}
</script>

<style scoped>
.card {
  width: 200px;
  height: 232px;
  border: 2px solid black;
  border-radius: 5px;
  transition: box-shadow .5s;
  margin-left: 10px;
  margin-right: 10px;
  background-image: url("../../assets/vue-js-egitim-background.jpg");
  background-size: cover;
  background-repeat: no-repeat;
  background-position: center;
  box-shadow: 0px 5px 48px #666;
}

.default-card{
  width: 200px;
  height: 232px;
  border: 2px solid black;
  border-radius: 5px;
  transition: box-shadow .5s;
  margin-left: 10px;
  margin-right: 10px;
  background-size: cover;
  background-repeat: no-repeat;
  background-position: center;
  box-shadow: 0px 5px 48px #666;
}
</style>
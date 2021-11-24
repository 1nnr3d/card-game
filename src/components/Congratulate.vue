<template>
  <div class="container">
    <div id="tsparticles"></div>
    <h1 class="title">Kazandınız!!</h1>
    <p class="description">Tekrar oynamak ister misiniz ?</p>
    <button @click="resetGame" class="restart-button"> Tekrar Oyna</button>
  </div>
</template>

<script>
import eventBus from "../eventBus";

export default {
  methods: {
    resetGame: function () {
      eventBus.$emit('restartGame', 'app-game-cards')
    }
  },
  created(){
    var end = Date.now() + (10 * 1000);

// go Buckeyes!
    var colors = ['#bb0000', '#84fc02', '#0335f5'];

    (function frame() {
      confetti({
        particleCount: 3,
        angle: 55,
        spread: 60,
        origin: {x: 0},
        colors: colors
      });
      confetti({
        particleCount: 3,
        angle: 130,
        spread: 60,
        origin: {x: 1},
        colors: colors
      });

      if (Date.now() < end) {
        requestAnimationFrame(frame);
      }
    }());
  }
}
</script>

<style scoped>
.container {
  background-color: rgba(107, 107, 107, 0.09);
  display: block;
  margin-top: 16%;
  margin-left: auto;
  margin-right: auto;
  padding: 70px 0px;
  width: 400px;
  font-family: sans-serif;
  border: 1px solid rgba(128, 128, 128, 0.19);
  border-radius: 15px;
}

.title {
  text-align: center;
  font-size: 42px;
}

.description {
  text-align: center;
  margin-bottom: 20px;
}

.restart-button {
  display: block;
  margin-left: auto;
  margin-right: auto;
  width: 200px;
  height: 30px;
  background-color: #75fc32;
  border: none;
  border-radius: 10px;
  font-size: 14px;
  cursor: pointer;
  transition: .4s;
}

.restart-button:hover {
  color: white;
  background-color: #dadada;
}
</style>
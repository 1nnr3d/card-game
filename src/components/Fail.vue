<template>
  <div class="container">
    <h1 class="title">Kaybettiniz!</h1>
    <p class="description">Tekrar oynamak ister misiniz ?</p>
    <button @click="resetGame" class="restart-button"> Tekrar Oyna </button>
    <p></p>
  </div>
</template>

<script>
import eventBus from "../eventBus";

export default {
  methods: {
    resetGame: function () {
      eventBus.$emit('restartGame', 'app-game-cards')
    }
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

.title{
  text-align: center;
  font-size: 42px;
}

.description{
  text-align: center;
  margin-bottom: 20px;
}

.restart-button{
  display: block;
  margin-left: auto;
  margin-right: auto;
  width: 200px;
  height: 30px;
  background-color: #f82b41;
  border: none;
  border-radius: 10px;
  font-size: 14px;
  color: white;
  cursor: pointer;
  transition: .4s;
}

.restart-button:hover{
  color: #f82b41;
  background-color: #dadada;
}
</style>
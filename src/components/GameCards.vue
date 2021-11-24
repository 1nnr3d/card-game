<template>
  <div class="game-area">
    <h1 class="title">Kedi <span>Nerede</span> <strong>?</strong></h1>
    <h4 class="description">Açık kartlardan birini seçtikten sonra, kapalı olan karta tıklayınız.</h4>
    <div class="container">
      <transition-group enter-active-class="animate__animated animate__rotateIn"
                        leave-active-class="animate__animated animate__rotateIn"
                        class="container"
                        appear>
        <app-card
            :key="card"
            :class="{'shadow': selectedCard == card}"
            @click.native="selectedCard = card"
            v-for="card in 5"
            :number="card">
        </app-card>
      </transition-group>
    </div>
    <div class="container">
      <app-default-card :default="defaultCard" :selected="selectedCard"></app-default-card>
    </div>
  </div>
</template>

<script>
import Card from "./Partials/Card";
import DefaultCard from "./Partials/DefaultCard";

export default {
  data: function () {
    return {
      selectedCard: null,
      defaultCard: null
    }
  },
  components: {
    "app-card": Card,
    "app-default-card": DefaultCard
  },
  created() {
    this.defaultCard = Math.ceil(Math.random() * 5);
    console.log(this.defaultCard)
  }
}
</script>

<style scoped>
.title {
  text-align: center;
  color: crimson;
  margin-top: 70px;
}

.title span {
  color: dodgerblue;
}

.title strong {
  color: firebrick;
}

.description {
  color: gray;
  text-align: center;
}

.container {
  margin-top: 60px;
  display: flex;
  justify-content: center;
  align-content: center;
}

.shadow {
  box-shadow: 0px 0px 38px blueviolet !important;
  transition: .5s;
}

</style>
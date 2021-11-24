<template>
  <div class="card">
    <img :src="card" alt="">
  </div>
</template>

<script>
export default {
  data: function () {
    return {
      card: `src/assets/card-${this.number}.jpg`
    }
  },
  props: ["number"]
}
</script>

<style scoped>
.card {
  width: 200px;
  height: 232px;
  border: 2px solid black;
  border-radius: 5px;
  transition: box-shadow .5s;
  margin-left: 30px;
  margin-right: 30px;
  cursor: pointer;
}

.card:hover {
  box-shadow: 0px 5px 48px #666;
}

.card img {
  width: 100%;
  height: 100%;
}
</style>
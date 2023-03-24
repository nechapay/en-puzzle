<script setup>
let props = defineProps(['score'])
</script>

<template>
  <div class="final-page fill">
    <div class="final-page__header">Congratulations!<br />Your score: {{ props.score }}</div>
  </div>
</template>

<style scoped>
.final-page {
  /* background-image: linear-gradient(rgba(255, 255, 255, 0.1), rgba(255, 255, 255, 0.3)), url('/img/bg.png'); */
  background: linear-gradient(rgba(255, 255, 255, 0.3), rgba(255, 255, 255, 0.5));
  background-repeat: no-repeat;
  background-size: cover;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  position: fixed;
  top: 0;
  left: 0;
  color: rgb(224, 175, 13);
  z-index: 5;
  text-shadow: 1px 1px 2px black;
}

.final-page__header {
  font-size: 600%;
  margin-bottom: 10vmin;
  text-align: center;
}
.final-page__body {
  font-size: 300%;
  margin-bottom: 3vmin;
  text-align: center;
}
</style>

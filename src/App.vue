<script setup>
import { ref } from 'vue'

import MainPage from './components/MainPage.vue'
import EndPage from './components/EndPage.vue'
import Copyright from './components/Copyright.vue'

let started = ref(true)
let ended = ref(false)
let score = ref(0)

function handleEnd(val) {
  score.value = val
  ended.value = true
}
</script>

<template>
  <div>
    <MainPage @finished="handleEnd" />
    <EndPage v-if="started && ended" :score="score" />
    <Copyright />
  </div>
</template>

<style scoped></style>

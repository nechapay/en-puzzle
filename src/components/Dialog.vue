<script setup>
import { ref } from 'vue'
const emit = defineEmits(['close', 'solved'])
const props = defineProps(['question'])
let penalty = ref(0)
let rotateAnswer = ref(false)
let rotateTips = ref(false)

let answerVisible = ref(false)

function handleAnswerClick() {
  rotateAnswer.value = true
  rotateTips.value = true
  answerVisible.value = true
}

function handleSolved(val) {
  if (val) {
    emit('solved', props.question.points - penalty.value)
  } else {
    emit('solved', 0)
  }
  resetDef()
}

function handleCloseClick() {
  if (answerVisible.value) emit('solved', 0)
  resetDef()
  emit('close')
}

function resetDef() {
  penalty.value = 0
  rotateAnswer.value = false
  rotateTips.value = false
  answerVisible.value = false
}

function showTips() {
  rotateTips.value = true
  penalty.value = 5
}
</script>

<template>
  <div class="dialog-container fill">
    <div class="dialog-wrapper">
      <div class="dialog-head">
        <div class="head-wrapper">
          <span>Вопрос за {{ props.question.points - penalty }} очков</span>
        </div>
        <button class="close-button" @click="handleCloseClick">X</button>
      </div>
      <div class="dialog-body">
        <div class="question-wrapper">
          <div class="question-text">
            {{ props.question.text }}
          </div>
          <div class="flip-card answer" :class="{ rotate: rotateAnswer }">
            <div class="flip-card-inner" :class="{ rotate: rotateAnswer }">
              <div class="flip-card-front"></div>
              <div class="flip-card-back">
                {{ props.question.answer }}
              </div>
            </div>
          </div>
        </div>
        <div class="tips-wrapper" v-if="props.question.tips">
          <div class="tips">
            <div class="flip-card tip" :class="{ rotate: rotateTips }" v-for="tip in props.question.tips">
              <div class="flip-card-inner" :class="{ rotate: rotateTips }">
                <div class="flip-card-front tip-front">Подсказка</div>
                <div class="flip-card-back tip-back">
                  <img :src="`/img/${tip}`" />
                </div>
              </div>
            </div>
          </div>
          <div class="tips-controls" v-if="!rotateTips">
            <button class="my-button" @click="showTips">Показать подсказку</button>
          </div>
        </div>
      </div>
      <div class="dialog-footer">
        <button class="my-button" @click="handleAnswerClick" v-if="!answerVisible">Показать ответ</button>
        <div v-else class="buttons-wrapper">
          <button class="my-button correct" @click="handleSolved(true)">Верно</button>
          <button class="my-button incorrect" @click="handleSolved(false)">Неверно</button>
        </div>
      </div>
    </div>
  </div>
</template>

<style lang="css" scoped>
.dialog-container {
  display: flex;
  align-items: center;
  justify-content: center;
  position: fixed;
  top: 0;
  left: 0;
  z-index: 99;
  background: rgba(119, 117, 117, 0.555);
}

.dialog-wrapper {
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  width: 70%;
  height: 70%;
  background: white;
  box-shadow: 2px 4px 10px black;
}

.dialog-head {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 100%;
  height: 10%;
  font-size: 200%;
  font-weight: bolder;
}

.head-wrapper {
  display: flex;
  align-items: center;
  justify-content: center;
  margin-left: 2%;
  width: 100%;
  height: 100%;
  border-bottom: 1px solid black;
}

.dialog-body {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 100%;
  height: 80%;
}

.dialog-footer {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 100%;
  height: 10%;
}

.close-button {
  display: flex;
  align-items: center;
  justify-content: center;
  border: none;
  cursor: pointer;
  padding: 20px;
  justify-self: flex-end;
  align-self: flex-start;
  position: relative;
  top: 0;
  font-size: 1rem;
  font-weight: bolder;
  background: none;
}

.close-button:hover {
  background: red;
  color: white;
}

.flip-card {
  background-color: transparent;
  width: 100%;
  height: 100%;
  perspective: 1000px;
}

.flip-card-inner {
  position: relative;
  width: 100%;
  height: 100%;
  text-align: center;
  transition: transform 0.8s;
  transform-style: preserve-3d;
}

.flip-card-front,
.flip-card-back {
  position: absolute;
  width: 100%;
  height: 100%;
  -webkit-backface-visibility: hidden; /* Safari */
  backface-visibility: hidden;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.flip-card-front {
  transition-duration: 0.5s;
}

.flip-card-back {
  transform: rotateX(180deg);
}

.flip-card.rotate .flip-card-inner {
  transform: rotateX(180deg);
}

.my-button {
  padding: 10px 20px;
  border: 1px solid rgb(0, 110, 255);
  background: white;
  transition-duration: 0.5s;
  min-width: 200px;
  font-size: 1.5rem;
  margin-left: 2%;
}

.my-button:hover {
  background: rgb(0, 110, 255);
  color: white;
}

.my-button.correct {
  border: 1px solid rgb(0, 128, 64);
}

.my-button.correct:hover {
  background: rgb(0, 128, 64);
  color: white;
}

.my-button.incorrect {
  border: 1px solid rgb(255, 38, 0);
}

.my-button.incorrect:hover {
  background: rgb(255, 38, 0);
  color: white;
}

.buttons-wrapper {
  display: flex;
  width: 100%;
  height: 100%;
  justify-content: center;
  align-items: center;
}

.question-wrapper {
  display: flex;
  flex-direction: column;
  width: 70%;
  height: 100%;
  align-items: center;
  justify-content: center;
}

.question-text,
.answer {
  width: 100%;
  height: 50%;
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 200%;
  padding: 5%;
  text-align: center;
}

.tips-wrapper {
  display: flex;
  width: 30%;
  height: 100%;
  flex-direction: column;
  justify-content: center;
}
.tip {
  width: 90%;
  height: 90%;
  margin: 5%;
}
.tip-front {
  font-size: 2rem;
  border: 1px dotted black;
}

.tip-back img {
  height: 100%;
  max-width: 100%;
}

.tips {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  width: 100%;
  height: 90%;
}

.tips-controls {
  display: flex;
  align-items: center;
  justify-content: center;
}
</style>

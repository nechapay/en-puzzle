<script setup>
import { ref, watch } from 'vue'
import Dialog from './Dialog.vue'

const cards = [
  {
    id: 1,
    class: 'category-one',
    sub: [
      {
        id: 11,
        text: '1',
        class: ref({
          'bg-11': true,
          hide: false
        }),
        rotate: ref(false),
        question: {
          answer: 'Kingfisher',
          points: 10,
          text: 'What bird helps solve a problem with high speed trains?',
          tips: ['cat1-1.png', 'cat1-2.png']
        }
      },
      {
        id: 12,
        text: '2',
        rotate: ref(false),
        class: ref({
          'bg-12': true,
          hide: false
        }),
        question: {
          answer: 'The combination of spongy skull bones and a tough, elastic beak.',
          points: 10,
          text: 'How did the woodpecker inspire scholars to create shock-absorbing technology?',
          tips: ['cat1-3.png', 'cat1-4.png']
        }
      },
      {
        id: 13,
        text: '3',
        rotate: ref(false),
        class: ref({
          'bg-13': true,
          hide: false
        }),
        question: {
          answer: 'Because of humming bird’s precise and quick maneuvering abilities.',
          points: 10,
          text: 'Why is a hovering drone similar to a flitting hummingbird?',
          tips: ['cat1-5.png', 'cat1-6.png']
        }
      },
      {
        id: 14,
        text: '4',
        rotate: ref(false),
        class: ref({
          'bg-14': true,
          hide: false
        }),
        question: {
          answer: 'Falcon',
          points: 10,
          text: 'Whose shape in flight inspired the aerodynamic form of the B-2 bomber?',
          tips: ['cat1-7.png', 'cat1-8.png']
        }
      }
    ]
  },
  {
    id: 2,
    class: 'category-two',
    sub: [
      {
        id: 21,
        text: '1',
        rotate: ref(false),
        class: ref({
          'bg-21': true,
          hide: false
        }),
        question: {
          answer: 'Frank Fish, a professor of Biology from West Chester University.',
          points: 10,
          text: 'Who worked out a way of adding whale’s bumps to wind turbine blades?',
          tips: ['cat2-1.png', 'cat2-2.png']
        }
      },
      {
        id: 22,
        text: '2',
        rotate: ref(false),
        class: ref({
          'bg-22': true,
          hide: false
        }),
        question: {
          answer: 'Squid’s skin is able to disguise effectively.',
          points: 10,
          text: 'Why do the military men use the squid’s skills?',
          tips: ['cat2-3.png', 'cat2-4.png']
        }
      },
      {
        id: 23,
        text: '3',
        rotate: ref(false),
        class: ref({
          'bg-23': true,
          hide: false
        }),
        question: {
          answer: 'A material, known as Sharklet that optimizes vessel performance and reduces fuel costs.',
          points: 10,
          text: 'What material optimizes vessel performance and reduces fuel costs?',
          tips: ['cat2-5.png', 'cat2-6.png']
        }
      },
      {
        id: 24,
        text: '4',
        rotate: ref(false),
        class: ref({
          'bg-24': true,
          hide: false
        }),
        question: {
          answer: 'The seahorse’s tail-gripping mechanism and its flexibility.',
          points: 10,
          text: 'How did precise movements of the seahorse inspire scientists to create the robotic arm?',
          tips: ['cat2-7.png', 'cat2-8.png']
        }
      }
    ]
  },
  {
    id: 3,
    class: 'category-three',
    sub: [
      {
        id: 31,
        text: '1',
        rotate: ref(false),
        class: ref({
          'bg-31': true,
          hide: false
        }),
        question: {
          answer: 'Zinc atoms (tiny particles) spread around the ants teeth.',
          points: 10,
          text: 'Why can ants’ teeth cut things efficiently without damaging?',
          tips: ['cat3-1.png', 'cat3-2.png']
        }
      },
      {
        id: 32,
        text: '2',
        rotate: ref(false),
        class: ref({
          'bg-32': true,
          hide: false
        }),
        question: {
          answer: 'Snake',
          points: 10,
          text: 'What animal helped scientists design new, hard-wearing paints and surfaces?',
          tips: ['cat3-3.png', 'cat3-4.png']
        }
      },
      {
        id: 33,
        text: '3',
        rotate: ref(false),
        class: ref({
          'bg-33': true,
          hide: false
        }),
        question: {
          answer: 'With the help of amazing gloves that imitate thousands of tiny elastic hairs on gecko’s feet.',
          points: 10,
          text: 'In what way did gecko’s feet help military climb over tough uneven surfaces?',
          tips: ['cat3-5.png', 'cat3-6.png']
        }
      },
      {
        id: 34,
        text: '4',
        rotate: ref(false),
        class: ref({
          'bg-34': true,
          hide: false
        }),
        question: {
          answer: 'Swiss engineer George de Mestral.',
          points: 10,
          text: 'Who invented Velcro as a way to easily fasten things together?',
          tips: ['cat3-7.png', 'cat3-8.png']
        }
      }
    ]
  },
  {
    id: 4,
    class: 'category-four',
    sub: [
      {
        id: 41,
        text: '1',
        rotate: ref(false),
        class: ref({
          'bg-41': true,
          hide: false
        }),
        question: {
          answer: "A learning about  emulating nature's forms to create more sustainable designs and technologies.",
          points: 10,
          text: 'What is biomimicry?',
          tips: ['cat4-1.png', 'cat4-2.png']
        }
      },
      {
        id: 42,
        text: '2',
        rotate: ref(false),
        class: ref({
          'bg-42': true,
          hide: false
        }),
        question: {
          answer: 'Janine Benyus, an American natural sciences writer.',
          points: 10,
          text: 'Who coined the term biomimicry?',
          tips: ['cat4-3.png', 'cat4-4.png']
        }
      },
      {
        id: 43,
        text: '3',
        rotate: ref(false),
        class: ref({
          'bg-43': true,
          hide: false
        }),
        question: {
          answer: "To learn from nature's wisdom, heal ourselves, fulfill the humans needs and develop technologies.",
          points: 10,
          text: 'Why is biomimicry used?',
          tips: ['cat4-5.png', 'cat4-6.png']
        }
      },
      {
        id: 44,
        text: '4',
        rotate: ref(false),
        class: ref({
          'bg-44': true,
          hide: false
        }),
        question: {
          answer: 'The Greek words bios, meaning life, and mimesis, meaning imitate.',
          points: 10,
          text: 'Where does the word biomimicry come from?',
          tips: ['cat4-7.png', 'cat4-8.png']
        }
      }
    ]
  }
]

const emit = defineEmits(['finished'])

let dialog = ref(false)
let dialogData = ref({})
let currentId = 0
let score = ref(0)
let solvedCount = ref(0)
let solved = ref(false)

function handleSubClick(val) {
  if (!val.class.value.hide) {
    currentId = val.id
    dialogData.value = val.question
    dialog.value = true
  }
}

watch(solvedCount, (newVal, oldVal) => {
  if (newVal !== oldVal && newVal >= cards.length * 4) {
    console.log('game over')
    solved.value = true
    emit('finished', score)
  }
})

function handleClose(val) {
  cards.forEach((item) => {
    item.sub.forEach((sub) => {
      if (sub.id === currentId) {
        sub.class.value.hide = true
      }
    })
  })
  dialog.value = false
  score.value += val
  solvedCount.value++
}
</script>
<template>
  <div class="highscore" v-show="!solved">Счёт - {{ score }}</div>
  <div class="container grid">
    <div class="category grid" v-for="card in cards" :key="card.id" :class="card.class">
      <div
        class="sub-category"
        v-for="sub in card.sub"
        :key="sub.id"
        :class="sub.class.value"
        @click="handleSubClick(sub)"
      >
        <span>{{ sub.text }}</span>
      </div>
    </div>
  </div>
  <Transition name="fade">
    <Dialog v-show="dialog" :question="dialogData" @solved="handleClose" @close="dialog = false" />
  </Transition>
</template>

<style lang="css" scoped>
.container {
  width: 96%;
  height: 50vw;
  border: 1px solid black;
  margin: 0 2% 2% 2%;
  background-repeat: no-repeat;
  background-image: url('/img/bg.png');
  background-size: cover;
}

.grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  grid-template-rows: 1fr 1fr;
}

.category {
  width: 100%;
  height: 100%;
}

.sub-category {
  font-size: 300%;
  color: white;
  text-shadow: 1px 1px 1px black;
  font-weight: bolder;
  user-select: none;
  border: 1px solid black;
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  cursor: pointer;
  transition-duration: 1.5s;
}

.category-one {
  background-repeat: no-repeat;
  /* background-repeat: no-repeat;
  background-image: url('/img/cat1.png');
  background-size: cover; */
}

.category-two {
  background-repeat: no-repeat;
  /* background-image: url('/img/cat2.png'); */
  background-size: cover;
}

.category-three {
  background-repeat: no-repeat;
  /* background-image: url('/img/cat3.png'); */
  background-size: cover;
}

.category-four {
  background-repeat: no-repeat;
  /* background-image: url('/img/cat4.png'); */
  background-size: cover;
}

.triangle-top {
  position: absolute;
  width: 100%;
  height: 100%;
  clip-path: polygon(0 0, 100% 0, 0 100%);
  background: yellow;
}

.triangle-bottom {
  position: absolute;
  width: 100%;
  height: 100%;
  clip-path: polygon(100% 0, 100% 100%, 0 100%);
  background: orangered;
}
.triangle-image {
  width: 100%;
  object-fit: contain;
}

.bg-11 {
  background-size: 200%;
  background-repeat: no-repeat;
  background-image: url('/img/cat1.png');
}

.bg-12 {
  background-size: 200%;
  background-repeat: no-repeat;
  background-image: url('/img/cat1.png');
  background-position: 100% 0%;
}

.bg-13 {
  background-size: 200%;
  background-repeat: no-repeat;
  background-image: url('/img/cat1.png');
  background-position: 0% 65%;
}

.bg-14 {
  background-size: 200%;
  background-repeat: no-repeat;
  background-image: url('/img/cat1.png');
  background-position: 100% 65%;
}

.bg-21 {
  background-size: 200%;
  background-repeat: no-repeat;
  background-image: url('/img/cat2.png');
}

.bg-22 {
  background-size: 200%;
  background-repeat: no-repeat;
  background-image: url('/img/cat2.png');
  background-position: 100% 0%;
}

.bg-23 {
  background-size: 200%;
  background-repeat: no-repeat;
  background-image: url('/img/cat2.png');
  background-position: 0% 86%;
}

.bg-24 {
  background-size: 200%;
  background-repeat: no-repeat;
  background-image: url('/img/cat2.png');
  background-position: 100% 86%;
}

.bg-31 {
  background-size: 200%;
  background-repeat: no-repeat;
  background-image: url('/img/cat3.png');
}

.bg-32 {
  background-size: 200%;
  background-repeat: no-repeat;
  background-image: url('/img/cat3.png');
  background-position: 100% 0%;
}

.bg-33 {
  background-size: 200%;
  background-repeat: no-repeat;
  background-image: url('/img/cat3.png');
  background-position: 0% 75%;
}

.bg-34 {
  background-size: 200%;
  background-repeat: no-repeat;
  background-image: url('/img/cat3.png');
  background-position: 100% 75%;
}

.bg-41 {
  background-size: 200%;
  background-repeat: no-repeat;
  background-image: url('/img/cat4.png');
}

.bg-42 {
  background-size: 200%;
  background-repeat: no-repeat;
  background-image: url('/img/cat4.png');
  background-position: 100% 0%;
}

.bg-43 {
  background-size: 200%;
  background-repeat: no-repeat;
  background-image: url('/img/cat4.png');
  background-position: 0% 75%;
}

.bg-44 {
  background-size: 200%;
  background-repeat: no-repeat;
  background-image: url('/img/cat4.png');
  background-position: 100% 75%;
}

.hide {
  opacity: 0;
  cursor: auto;
}

.highscore {
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 180%;
  font-weight: bolder;
  height: 2%;
}
</style>

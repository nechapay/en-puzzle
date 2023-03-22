<script setup>
import { ref } from 'vue'

const cards = [
  {
    id: 1,
    class: 'category-one',
    sub: [
      {
        id: 11,
        text: '1',
        rotate: ref(false),
        content: {
          top: {
            img: 'cat1-1.png',
            question: '1 - top'
          },
          bottom: {
            img: 'cat1-2.png',
            question: '1 - bottom'
          }
        }
      },
      {
        id: 12,
        text: '2',
        rotate: ref(false),
        content: {
          top: {
            img: 'cat1-3.png',
            question: '1 - top'
          },
          bottom: {
            img: 'cat1-4.png',
            question: '1 - bottom'
          }
        }
      },
      {
        id: 13,
        text: '3',
        rotate: ref(false),
        content: {
          top: {
            img: 'cat1-5.png',
            question: '1 - top'
          },
          bottom: {
            img: 'cat1-6.png',
            question: '1 - bottom'
          }
        }
      },
      {
        id: 14,
        text: '4',
        rotate: ref(false),
        content: {
          top: {
            img: 'cat1-7.png',
            question: '1 - top'
          },
          bottom: {
            img: 'cat1-8.png',
            question: '1 - bottom'
          }
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
        content: {
          top: {
            img: 'cat2-1.png',
            question: '1 - top'
          },
          bottom: {
            img: 'cat2-2.png',
            question: '1 - bottom'
          }
        }
      },
      {
        id: 22,
        text: '2',
        rotate: ref(false),
        content: {
          top: {
            img: 'cat2-3.png',
            question: '1 - top'
          },
          bottom: {
            img: 'cat2-4.png',
            question: '1 - bottom'
          }
        }
      },
      {
        id: 23,
        text: '3',
        rotate: ref(false),
        content: {
          top: {
            img: 'cat2-5.png',
            question: '1 - top'
          },
          bottom: {
            img: 'cat2-6.png',
            question: '1 - bottom'
          }
        }
      },
      {
        id: 24,
        text: '4',
        rotate: ref(false),
        content: {
          top: {
            img: 'cat2-7.png',
            question: '1 - top'
          },
          bottom: {
            img: 'cat2-8.png',
            question: '1 - bottom'
          }
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
        content: {
          top: {
            img: 'cat3-1.png',
            question: '1 - top'
          },
          bottom: {
            img: 'cat3-2.png',
            question: '1 - bottom'
          }
        }
      },
      {
        id: 32,
        text: '2',
        rotate: ref(false),
        content: {
          top: {
            img: 'cat3-3.png',
            question: '1 - top'
          },
          bottom: {
            img: 'cat3-4.png',
            question: '1 - bottom'
          }
        }
      },
      {
        id: 33,
        text: '3',
        rotate: ref(false),
        content: {
          top: {
            img: 'cat3-5.png',
            question: '1 - top'
          },
          bottom: {
            img: 'cat3-6.png',
            question: '1 - bottom'
          }
        }
      },
      {
        id: 34,
        text: '4',
        rotate: ref(false),
        content: {
          top: {
            img: 'cat3-7.png',
            question: '1 - top'
          },
          bottom: {
            img: 'cat3-8.png',
            question: '1 - bottom'
          }
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
        content: {
          top: {
            img: 'cat4.png',
            question: '1 - top'
          },
          bottom: {
            img: 'cat4.png',
            question: '1 - bottom'
          }
        }
      },
      {
        id: 42,
        text: '2',
        rotate: ref(false),
        content: {
          top: {
            img: 'cat4.png',
            question: '1 - top'
          },
          bottom: {
            img: 'cat4.png',
            question: '1 - bottom'
          }
        }
      },
      {
        id: 43,
        text: '3',
        rotate: ref(false),
        content: {
          top: {
            img: 'cat4.png',
            question: '1 - top'
          },
          bottom: {
            img: 'cat4.png',
            question: '1 - bottom'
          }
        }
      },
      {
        id: 44,
        text: '4',
        rotate: ref(false),
        content: {
          top: {
            img: 'cat4.png',
            question: '1 - top'
          },
          bottom: {
            img: 'cat4.png',
            question: '1 - bottom'
          }
        }
      }
    ]
  }
]

function blockRotation() {
  let result = false
  cards.forEach((item) => {
    item.sub.forEach((sub) => {
      if (sub.rotate.value) result = true
    })
  })
  return result
}

function rotateHandle(val) {
  if (!blockRotation()) {
    val.value = !val.value
  }
}

function handleTopClick(val) {
  console.log(val.question)
}

function handleBottomClick(val) {
  console.log(val.question)
}
</script>
<template>
  <div class="container grid">
    <div class="category grid" v-for="card in cards" :key="card.id" :class="card.class">
      <div
        class="flip-card sub-category"
        v-for="sub in card.sub"
        :key="sub.id"
        :class="{ rotate: sub.rotate.value }"
        @click="rotateHandle(sub.rotate)"
      >
        <div class="flip-card-inner" :class="{ rotate: sub.rotate.value }">
          <div class="flip-card-front">
            <span>{{ sub.text }}</span>
          </div>
          <div class="flip-card-back">
            <div class="triangle-top" @click="handleTopClick(sub.content.top)">
              <img class="triangle-image" :src="`/img/${sub.content.top.img}`" />
            </div>
            <div class="triangle-bottom" @click="handleBottomClick(sub.content.bottom)">
              <img class="triangle-image" :src="`/img/${sub.content.bottom.img}`" />
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style lang="css" scoped>
.container {
  width: 96%;
  height: 50vw;
  border: 1px solid black;
  margin: 2%;
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

.category-one {
  background-repeat: no-repeat;
  background-image: url('/img/cat1.png');
  background-size: cover;
}

.category-one.clipped {
  clip-path: polygon(50% 0, 100% 0, 100% 100%, 0 100%, 0 50%, 50% 50%);
}

.category-two {
  background-repeat: no-repeat;
  background-image: url('/img/cat2.png');
  background-size: cover;
}

.category-three {
  background-repeat: no-repeat;
  background-image: url('/img/cat3.png');
  background-size: cover;
}

.category-four {
  background-repeat: no-repeat;
  background-image: url('/img/cat4.png');
  background-size: cover;
}

.flip-card {
  background-color: transparent;
  width: 100%;
  height: 100%;
  /* border: 1px solid black; */
  /* border-radius: 5px; */
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
  border: 1px solid black;
}

.flip-card-back {
  transform: rotateX(180deg);
  background: wheat;
}

.flip-card.rotate .flip-card-inner {
  transform: rotateX(180deg);
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
</style>

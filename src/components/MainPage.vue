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
        rotate: ref(false)
      },
      {
        id: 12,
        text: '2',
        rotate: ref(false)
      },
      {
        id: 13,
        text: '3',
        rotate: ref(false)
      },
      {
        id: 14,
        text: '4',
        rotate: ref(false)
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
        rotate: ref(false)
      },
      {
        id: 22,
        text: '2',
        rotate: ref(false)
      },
      {
        id: 23,
        text: '3',
        rotate: ref(false)
      },
      {
        id: 24,
        text: '4',
        rotate: ref(false)
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
        rotate: ref(false)
      },
      {
        id: 32,
        text: '2',
        rotate: ref(false)
      },
      {
        id: 33,
        text: '3',
        rotate: ref(false)
      },
      {
        id: 34,
        text: '4',
        rotate: ref(false)
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
        rotate: ref(false)
      },
      {
        id: 42,
        text: '2',
        rotate: ref(false)
      },
      {
        id: 43,
        text: '3',
        rotate: ref(false)
      },
      {
        id: 44,
        text: '4',
        rotate: ref(false)
      }
    ]
  }
]

let rotate = {
  one: ref(false),
  two: ref(false),
  three: ref(false),
  four: ref(false)
}
function rotateHandle(val) {
  console.log(val)
  val.value = !val.value
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
          <div class="flip-card-back"></div>
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
  background: grey;
}

.category-two {
  background: blue;
}

.category-three {
  background: green;
}

.category-four {
  background: red;
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

/* .flip-card-front {
} */

.flip-card-back {
  transform: rotateX(180deg);
  background: wheat;
}

.flip-card.rotate .flip-card-inner {
  transform: rotateX(180deg);
}
</style>

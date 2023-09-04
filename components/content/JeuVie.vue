<template>
  <div class="content">
    <div class="buttons">
      <button v-if="play" @click="playSimulation()" class="play-button">Play</button>
      <button v-if="reset" @click="resetSimulation()" class="reset-button">Reset</button>
    </div>
    <div class="unicell" :style="{ 'justify-content': jc }">
      <span v-if="gen" class="gen">Gen. {{ gen }}</span>
      <div v-for="(cll, index) in arrGen" :key="index" class="cell" :class="{ 'alive': cll, 'dead': !cll }"
        @click="toggleCell(index)"></div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';

const props = defineProps({
  code: String,
  gen: String,
  jc: String,
  play: String,
  reset: String,
  step: String
});

let arrGen = ref(props.code ? props.code.split('').map(c => c === '1') : []);

const originalArrGen = ref([...arrGen.value]); // Create a deep copy or the original array


function playSimulation(generation : number) {
  const newArray = ref([...arrGen.value]);

  for (let i = 0; i < arrGen.value.length; i++) {
    let cells = [];
    if (i > 0) {
      cells.push(arrGen.value[i - 1]);
    }

    if (i < arrGen.value.length - 1) {
      cells.push(arrGen.value[i + 1]);
    }


    if (arrGen.value[i] === false) {
      let a = 0;
      cells.forEach(v => {
        if (v === true) {
          a++
        };
      })
      if (a != 0) {
        newArray.value[i] = !newArray.value[i];
      }
    }
  }
  arrGen.value = [...newArray.value];
}

function resetSimulation() {
  arrGen.value = [...originalArrGen.value];
}

function toggleCell(index: string | number) {
  arrGen.value[index] = !arrGen.value[index];
}
</script>

<style scoped>
.content {
  width: 100%;
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: center;
}

.buttons {
  position: absolute;
  left: 0;
}

.play-button {
  background-color: darkgreen;
  color: white;
  border: none;
  padding: 5px 15px;
  margin-right: 10px;
  border-radius: 5px;
  cursor: pointer;
}

.reset-button {
  background-color: darkred;
  color: white;
  border: none;
  padding: 5px 15px;
  border-radius: 5px;
  cursor: pointer;
}

.cell {
  width: 2rem;
  height: 2rem;
  display: inline;
  border: 1px solid black;
  border-radius: 5px;
  margin: 0.2rem;
}

.dead {
  background-color: white;
}

.alive {
  background-color: black;
}

.gen {
  color: red;
  margin-right: 1rem;
}

.unicell {
  margin-left: 1vw;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>

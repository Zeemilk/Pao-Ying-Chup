<template>
  <div id="world">
    <div id="fighter">
      <img id="Red" class="image" :src="redImage" alt="Red">
      <img id="Blue" class="image" :src="blueImage" alt="Blue">
    </div>
    <button @click="fight">สู้กัน</button>

    <div id="score">กระต่าย {{ red_score }} เต่า {{ blue_score }}</div>

    <button @click="reset">Reset</button>
    
  </div>
</template>

<script setup>
import { ref } from 'vue';

const red_score = ref(0);
const blue_score = ref(0);

const rpg = {
  1: 'kon.png',
  2: 'kradad.png',
  3: 'kunkrai.png'
};

const redImage = ref('kratai.jpg');
const blueImage = ref('tao.JPG');

function getRandomRpgImage() {
  const keys = Object.keys(rpg);
  const randomKey = keys[Math.floor(Math.random() * 3)];
  return rpg[randomKey];
}

function fight() {
  redImage.value = getRandomRpgImage();
  blueImage.value = getRandomRpgImage();
  
  if (redImage.value === 'kon.png' && blueImage.value === 'kradad.png'){
    blue_score.value++;
  }
  if (redImage.value === 'kon.png' && blueImage.value === 'kunkrai.png'){
    red_score.value++;
  }
  if (redImage.value === 'kradad.png' && blueImage.value === 'kon.png'){
    red_score.value++;
  }
  if (redImage.value === 'kradad.png' && blueImage.value === 'kunkrai.png'){
    blue_score.value++;
  }
  if (redImage.value === 'kunkrai.png' && blueImage.value === 'kon.png'){
    blue_score.value++;
  }
  if (redImage.value === 'kunkrai.png' && blueImage.value === 'kradad.png'){
    red_score.value++;
  }
}
function reset(){
  red_score.value = 0;
  blue_score.value = 0;
  redImage.value = 'kratai.jpg';
  blueImage.value = 'tao.JPG';
}
</script>

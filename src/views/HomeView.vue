<script setup>
import { ref } from 'vue'
import NavBar from '@/components/NavBar.vue'
import LogoBox from '@/components/LogoBox.vue'

const score = ref(0);
const streak = ref(0);

function updateScoreAndStreak({ correct }) {
  if (correct) {
    score.value += 1;
    streak.value += 1;
  } else {
    streak.value = 0;
  }

  console.log('Score Updated')
}
</script>

<template>
    <NavBar :score="score" :streak="streak" />
    <LogoBox @updateScoreAndStreak="updateScoreAndStreak" />
</template>
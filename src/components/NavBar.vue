<script setup>
import { ref } from 'vue';

defineProps({
  score: Number,
  streak: Number,
})

const isPlaying = ref(true);
const time = ref('1:00');

const toggleIsPlaying = () => {
  isPlaying.value = !isPlaying.value;
}


</script>

<template>
  <nav class="navbar">
    <div class="nav-left">
      <i :class="['pi', isPlaying ? 'pi-pause-circle': 'pi-play-circle', 'is-playing']" @click="toggleIsPlaying" :aria-label="isPlaying ? 'Pause' : 'Play'"></i>
      <span class="score">{{ score }}</span>
      <div class="streak">STREAK: x<span>{{ streak }}</span></div>
    </div>
    <div class="nav-right">
      <span class="time">{{ time }}</span>
    </div>
  </nav>
</template>

<style scoped>
.navbar {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 10px 20px;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
  z-index: 1000;
}

.nav-left,
.nav-right,
.streak {
  display: flex;
  align-items: center;
}

.is-playing {
  margin-right: 8px;
  cursor: pointer;
}

.score {
  margin-right: 8px;
}


.time {
  font-size: 1.2rem;
  font-weight: bold;
  margin-right: 25px;
}
</style>

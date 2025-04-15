<script setup>
import { ref , defineEmits} from 'vue';

const emit = defineEmits(['updateScoreAndStreak'])

const icons = import.meta.glob('../assets/icons/*.svg', { eager: true });

const iconsEntries = Object.entries(icons).map(([path, icon]) => ({
  name: path.split('/').pop().replace('.svg', ''),
  path: icon.default,
}));

function getRandomLogo () {
  const randomIndex = Math.floor(Math.random() * iconsEntries.length);
  return iconsEntries[randomIndex];
}

const selectedLogo = ref(getRandomLogo());
const options = ref([]);

function generateOptions () {
  const correctOption = selectedLogo.value;
  const shuffledIcons = [...iconsEntries].sort(() => Math.random() - 0.5);
  const randomOptions = shuffledIcons
    .filter(icon => icon.name !== correctOption.name)
    .slice(0, 3);
  options.value = [...randomOptions, correctOption].sort(() => Math.random() - 0.5);
}

function switchLogo() {
  selectedLogo.value = getRandomLogo();
  generateOptions();
}

function checkAnswer(selectedName) {
  if (selectedName === selectedLogo.value.name) {
    emit('updateScoreAndStreak', { correct: true });
  } else {
    emit('updateScoreAndStreak', { correct: false })
  }

  switchLogo();
}

generateOptions();
</script>

<template>
  <div class="logo-container">
    <img :src="selectedLogo.path" alt="Logo" class="logo" />
  </div>

  <div class="answer-container">
    <div
      v-for="option in options"
      :key="option.name"
      class="answer-option"
      @click="checkAnswer(option.name)">
      {{ option.name }}
    </div>
  </div>
</template>

<style scoped>
.logo-container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  height: 45vh;
  background-color: #f9f9f9;
}

.logo {
  width: 150px;
  height: auto;
}

button {
  margin-top: 15px;
}

.answer-container {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 10px;
  justify-items: stretch;
  align-items: stretch;
  height: 35vh;
  background-color: #f0f0f0;
  padding: 20px;
}

.answer-option {
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 1rem;
  cursor: pointer;
  background-color: #ffffff;
  border: 1px solid #ccc;
  border-radius: 5px;
  transition: background-color 0.3s;
  text-align: center;
  text-transform: uppercase;
}

.answer-option:hover {
  background-color: #f0f0f0;
}
</style>

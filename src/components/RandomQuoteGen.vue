<script setup>
import { ref, onMounted } from "vue";

const quotes = ref([
  {
    text: "The only way to do great work is to love what you do.",
    author: "Steve Jobs",
  },
  {
    text: "Believe you can and you're halfway there.",
    author: "Theodore Roosevelt",
  },
  {
    text: "Life is what happens when you're busy making other plans.",
    author: "John Lennon",
  },
]);

const currentQuote = ref({ text: "", author: "" });

const getRandomQuote = () => {
  const randomIndex = Math.floor(Math.random() * quotes.value.length);
  currentQuote.value = quotes.value[randomIndex];
};

onMounted(getRandomQuote);
</script>

<template>
  <div class="app">
    <h1 class="app-title">✨ Random Quote Generator ✨</h1>

    <transition name="fade" mode="out-in">
      <blockquote class="quote-card" :key="currentQuote.text">
        <p class="quote-text">“{{ currentQuote.text }}”</p>
        <cite class="quote-author">— {{ currentQuote.author }}</cite>
      </blockquote>
    </transition>

    <button @click="getRandomQuote" class="quote-button">
      🔁 New Quote
    </button>
  </div>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;600&display=swap');

.app {
  font-family: 'Inter', sans-serif;
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  background: linear-gradient(135deg, #89f7fe 0%, #66a6ff 100%);
  padding: 20px;
  text-align: center;
}

.app-title {
  font-size: 2rem;
  margin-bottom: 30px;
  color: #ffffff;
  text-shadow: 0 2px 8px rgba(0, 0, 0, 0.2);
}

.quote-card {
  background: rgba(255, 255, 255, 0.15);
  backdrop-filter: blur(14px);
  border-radius: 20px;
  padding: 30px;
  max-width: 500px;
  width: 100%;
  box-shadow: 0 8px 32px rgba(0, 0, 0, 0.2);
  color: #fff;
  margin-bottom: 20px;
  transition: all 0.3s ease-in-out;
}

.quote-text {
  font-size: 1.5rem;
  font-weight: 600;
  margin-bottom: 15px;
}

.quote-author {
  font-size: 1rem;
  color: #e0e0e0;
  font-style: normal;
}

.quote-button {
  background-color: #ffffff;
  color: #3498db;
  padding: 12px 24px;
  font-size: 16px;
  font-weight: bold;
  border: none;
  border-radius: 30px;
  cursor: pointer;
  transition: all 0.3s ease;
}

.quote-button:hover {
  background-color: #3498db;
  color: #ffffff;
  box-shadow: 0 4px 14px rgba(0, 0, 0, 0.25);
}

/* Animations */
.fade-enter-active, .fade-leave-active {
  transition: opacity 0.5s ease;
}
.fade-enter-from, .fade-leave-to {
  opacity: 0;
}
</style>

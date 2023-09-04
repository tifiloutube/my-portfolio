<script setup lang="ts">
import { onMounted, reactive, toRefs } from 'vue';

const state = reactive({
  buttonClass: 'hidden',
});

const { buttonClass } = toRefs(state);

let totalDuration = 0;

onMounted(() => {
  const words = ['WELCOME', 'TO', 'MY', 'PORTFOLIO'];
  let totalDuration = 0;

  function getRandomChar() {
    const chars = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ';
    return chars[Math.floor(Math.random() * chars.length)];
  }


  words.forEach((word, wordIndex) => {
    const wordDelay = wordIndex * 1000; // 1 seconde entre chaque mot
    const spans = document.querySelectorAll(`.word-${wordIndex} span`);
    let lastCharDuration = 0;

    spans.forEach((span, spanIndex) => {
      const charInterval = setInterval(() => {
        span.textContent = getRandomChar();
      }, 100);

      const charDuration = 1000 + (spanIndex * 200); // 1s + 0.2s par lettre

      // On prend la durée du dernier caractère pour chaque mot
      lastCharDuration = charDuration;

      setTimeout(() => {
        clearInterval(charInterval);
        span.textContent = word[spanIndex];
      }, charDuration + wordDelay);
    });
  });

  // Fait apparaître le bouton après que toutes les animations soient terminées
  setTimeout(() => {
    state.buttonClass = 'visible';
  }, 7500); // +1 seconde pour un petit délai
});
</script>



<template>
  <section>
    <div class="preloader">
      <div class="preloader-worlds">
        <div class="word-0 h2"><span></span><span></span><span></span><span></span><span></span><span></span><span></span></div>
        <div class="word-1 h2"><span></span><span></span></div>
        <div class="word-2 h2"><span></span><span></span></div>
        <div class="word-3 h2"><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span></div>
      </div>
      <div>
        <button class="loaderButton" :class="buttonClass">
          <NuxtLink to="/home" class="buttonText">
            ENTER
          </NuxtLink>
        </button>
      </div>
    </div>
  </section>
</template>

<style scoped>
  .preloader {
    height: 100vh;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    .preloader-worlds {
      display: flex;
      gap: 50px;
    }
    .loaderButton {
      font-family: Bebas Neue, sans-serif;
      font-size: 30px;
      background: none;
      border: none;
      padding: 0;
      margin: 0;
      cursor: pointer;
      outline: inherit;
      .buttonText:hover {
        color: #ccc;
        transition: color 0.5s ease;
      }
    }
  }
  .hidden {
    opacity: 0;
  }
  .visible {
    opacity: 1;
    transition: opacity 0.5s ease-in-out;
  }
</style>
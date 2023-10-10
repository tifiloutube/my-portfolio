<script setup lang="ts">
import { gsap } from 'gsap';

onMounted(() => {
  // Animation pour la ligne
  gsap.fromTo('.line', {
    width: '0%'
  }, {
    duration: 3,
    width: '100%',
    ease: 'easeInOut',
    delay: 0.5
  });

  // Animation pour le titre
  gsap.from('.letToRightAnim' , {
    duration: 3,
    opacity: 0,
    x: '-50%',
    ease: 'power3.out',
    delay: 0.5
  })

  // Animation pour les li
  gsap.from('.interest', {
    duration: 3,
    opacity: 0,
    x: '50%',
    ease: 'power3.out',
    stagger: 0.5,
    delay: 0.5
  })
});
</script>

<template>
  <section class="container">
    <div class="wrapper">
      <div class="topBlock">
        <p class="topBlock-text">About me</p>
        <span class="line letToRightAnim"></span>
      </div>
      <h2 class="h2 title letToRightAnim">Vilarinho Philippe</h2>
      <div class="description">
        <section>
          <p>Frontend Developer</p>
          <p class="text letToRightAnim">Blending <span class="emoji">👋</span> creativity with functionality, I craft robust web interfaces with a splash of artistry. My passion lies in elevating the aesthetic appeal of digital platforms, while maintaining a strong focus on usability. Currently honing my skills at Ynov Toulouse in web development, I thrive on the frontier of creative front-end development. My educational journey has been an arena to experiment, learn, and collaborate, fueling my enthusiasm to take on intricate web projects. With every line of code, I strive to push the envelope, aspiring to collaborate with innovative teams and clients to bring unique digital experiences to life.</p>
        </section>
        <article>
          <ul class="listInterest">
            <li>
              Interest
            </li>
            <li class="interest">
              Frontend Developer
            </li>
            <li class="interest">
              Creative Development
            </li>
            <li class="interest">
              Art Direction
            </li>
            <li class="interest">
              Chess
            </li>
          </ul>
        </article>
      </div>
    </div>
  </section>
</template>

<style scoped>
.container {
  height: calc(100vh - 175px);
  padding-top: 55px;
  .title {
    margin-top: 20px;
  }
  .topBlock {
    display: grid;
    gap: 8px;
    .topBlock-text {
      margin: 0;
    }
  }

  .line {
    display: inline-block;
    height: 1px;
    background-color: #F4EDDE;
    width: 100%;
  }

  .description {
    display: flex;
    gap: 180px;

    .listInterest {
      min-width: 160px;
      list-style: none;
      display: flex;
      flex-direction: column;
      gap: 8px;
      :nth-child(1) {
        text-decoration-line: underline;
      }
    }
  }
}

@keyframes waveAnimation {
  0% { transform: rotate(0deg); }
  50% { transform: rotate(-30deg); }
  100% { transform: rotate(0deg); }
}

.emoji {
  display: inline-block;
  animation: waveAnimation 3s infinite; /* 3s est la durée totale d'une vague complète, ajustez selon vos préférences */
}



/* Responsive Tablette */

@media screen and (max-width: 1024px) {
  .description {
    flex-direction: column;
    gap: 0 !important;
    .listInterest {
      padding: 0;
    }
  }
}

/* Responsive Mobile */

@media screen and (max-width: 600px) {

}
</style>
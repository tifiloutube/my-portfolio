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
          <p class="text letToRightAnim">
            Hey everyone! <span class="emoji">👋</span> It's a me, Mari... Uh no, wrong line. Hmm Hmm I am VILARINHO Philippe, a web developer with a passion for creative web development. Currently a student at Ynov Toulouse Campus, I am in search of an apprenticeship to enrich my master's journey. The endless possibilities of the web inspire me to push the boundaries and bring a creative touch to every project I work on.
            I am among those who believe that good energy and a relaxed atmosphere are essential for successful collaboration and continuous learning. I am always ready to learn, experiment, and share ideas with like-minded individuals.
            Thank you so much for reading! If you are curious to see what I have concocted so far, don't hesitate to click right here to browse through my projects. Looking forward to connecting and creating together!
          </p>
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
<script>
import { gsap } from 'gsap'

export default {
  mounted() {
    gsap.from('.title', {
      duration: 3,
      opacity: 0,
      y: '-50%',
      ease: 'power3.out'
    })

    gsap.from('.lineHome', {
      duration: 3,
      scaleX: 0,
      transformOrigin: 'left',
      ease: 'power3.out',
      delay: 1.5
    })
  }
}
</script>

<template>
    <section class="wrapper">
      <div class="container">
        <h1 class="h1 title">
          Vilarinho
          <span class="lineHome"></span>
          Philippe
        </h1>
      </div>
    </section>
</template>

<style scoped>
  .container {
    display: flex;
    align-items: start;
    padding-top: 40px;
    height: calc(100vh - 385px);
    .title {
      //margin-top: 0;
      display: flex;
      align-items: center;
      gap: 50px;
    }
    .lineHome {
      display: inline-block;
      width: calc(100vw - 1242px);
    }
  }
</style>
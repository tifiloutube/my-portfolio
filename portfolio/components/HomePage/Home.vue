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
          Vilarinho<span class="mobile-break"></span>
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
      width: 100%;
      display: flex;
      align-items: center;
      gap: 50px;
    }
    .lineHome {
      display: inline-block;
      width: calc(100vw - 1242px);
    }
    .mobile-break {
      display: none;
    }
  }

  @media screen and (max-width: 1024px) {
    .lineHome {
      min-width: calc(100vw - 820px);
    }
  }

  @media screen and (max-width: 600px) {
    .container {
      
    }
    .title {
      font-size: 100px !important;
      display: block !important;
    }
    .mobile-break {
      display: block !important;
      width: 100%;
    }
    .lineHome {
      display: none !important;
    }
  }
</style>
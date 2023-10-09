<script>
import { gsap } from 'gsap'

export default {
  mounted() {
    gsap.from('.left-block', {
      duration: 3,
      opacity: 0,
      x: '-50%',
      ease: 'power3.out',
      delay: 1.5
    })

    // Pour la ligne
    gsap.from('.right-block', {
      duration: 3,
      opacity: 0,
      x: '50%',
      ease: 'power3.out',
      delay: 1.5
    })
  }
}
</script>

<template>
  <footer class="wrapper footer">
    <div class="left-block">
      <div>
        <span>
          <svg width="6" height="7" viewBox="0 0 6 7" fill="none" xmlns="http://www.w3.org/2000/svg">
            <circle cx="3" cy="3.5" r="3" fill="white"/>
          </svg>
        </span>
        <p>info</p>
      </div>
      <div>
        Currently pursuing my web development studies at Ynov Toulouse, I am eagerly seeking a web development apprenticeship to further meld creativity with technical prowess in real-world projects.
      </div>
      <button class="custom-button" type="button">
        <NuxtLink to="/aboutme">
        explore
        <span>
          <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 20 20" fill="none">
            <path d="M12.0249 4.94168L17.0832 10L12.0249 15.0583" stroke="white" stroke-width="1.5" stroke-miterlimit="10" stroke-linecap="round" stroke-linejoin="round"/>
            <path d="M2.9165 10L16.9415 10" stroke="white" stroke-width="1.5" stroke-miterlimit="10" stroke-linecap="round" stroke-linejoin="round"/>
          </svg>
        </span>
        </NuxtLink>
      </button>
    </div>
    <div class="right-block">
      <ul class="right-block__list">
        <li>
          <NuxtLink to="https://github.com/tifiloutube" target="_blank">
            Github
          </NuxtLink>
        </li>
        <li>
          <NuxtLink href="https://www.linkedin.com/in/philippe-vilarinho-893a07161/" target="blank" class="link">
            LinkedIn
          </NuxtLink>
        </li>
      </ul>
    </div>
  </footer>
</template>

<style scoped>
  .footer {
    display: flex;
    justify-content: space-between;
    padding-bottom: 40px;
  }

  .left-block {
    width: 25%;
    min-width: 354px;
    padding: 16px;
    display: flex;
    flex-direction: column;
    gap: 16px;
    border-radius: 16px;
    background: rgba(53, 53, 53, 0.40);
    backdrop-filter: blur(12px);
    :nth-child(1) {
      display: flex;
      gap: 4px;
      :nth-child(1) {
        align-items: center;
      }
    }
    .custom-button {
      display: flex;
      gap: 4px;
      border: none;
      background-color: transparent;
      cursor: pointer;
    }
  }

  .right-block {
    display: flex;
    justify-content: flex-end;
    .right-block__list {
      list-style: none;
      display: flex;
      gap: 16px;
      align-items: flex-end;
    }
    .link {
      display: flex;
      gap: 10px;
    }
  }

  @media screen and (max-width: 600px) {
    .footer {
      display: grid;
      gap: 50px;
    }
    .left-block {
      min-width: 300px;
    }
    .right-block {
      .right-block__list {
        display: flex;
        justify-content: space-between;
        width: 100%;
        padding: 0;
        .link {
          gap: 0;
        }
      }
    }
  }

</style>
<template>
  <header class="wrapper header">
    <div class="logo always-on-top">
      <NuxtLink to="/home">
        <svg height="35" width="68">
          <text x="8.5" y="25" font-family="Verdana" font-size="24" fill="#F4EDDE">P</text>
          <text x="20" y="25" font-family="Verdana" font-size="24" fill="#F4EDDE">V</text>
          <text x="36" y="10" font-family="Verdana" font-size="8" fill="#F4EDDE">portfolio</text>
          <line x1="18.5" y1="10" x2="26.5" y2="25" style="stroke:#F4EDDE;stroke-width:0.3" />
        </svg>
      </NuxtLink>
    </div>
    <div class="location always-on-top">
      <NuxtLink to="https://earth.google.com/web/search/Toulouse/@43.59846655,1.46184695,168.36616161a,15081.47477419d,35y,50.81947276h,60t,0r/data=CigiJgokCSQGAkfr1TJAEQSri_ugxzLAGT4WeSz0wkhAIWhUdnsk-0jAKAI?hl=fr" target="_blank">
        currently living in <br>
        Toulouse, France
      </NuxtLink>
    </div>
    <div id="menu-icon" class="menu-icon always-on-top" @click="toggleMenu">
      <div>
        <svg xmlns="http://www.w3.org/2000/svg" width="7" height="8" viewBox="0 0 7 8" fill="none">
          <circle cx="3.5" cy="4" r="3.5" fill="#D9D9D9"/>
        </svg>
      </div>
      <div>
        <label id="menu-text">
          menu
        </label>
      </div>
    </div>

    <div id="fullscreen-menu" class="fullscreen-menu">
      <div class="wrapper fullscreen-menu__list">
        <ul>
          <li class="first anim-hover">
            <NuxtLink to="/home">
              <span class="anim-hover__line"></span>
              <p class="h2 anim-hover__title">Home</p>
            </NuxtLink>
          </li>
          <li class="second anim-hover">
            <NuxtLink to="/aboutme">
              <span class="anim-hover__line"></span>
              <p class="h2 anim-hover__title">About</p>
            </NuxtLink>
          </li>
          <li class="third anim-hover">
            <NuxtLink to="/work">
              <span class="anim-hover__line"></span>
              <p class="h2 anim-hover__title">Work</p>
            </NuxtLink>
          </li>
        </ul>
      </div>
    </div>
  </header>
</template>

<style lang="scss" scoped>
.header {
  position: relative;
  padding-top: 40px;
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  .location {
    text-align: center;
  }
  .menu-icon {
    display: flex;
    justify-content: flex-end;
    gap: 4px;
    div {
      display: flex;
      align-items: center;
    }
  }
  .always-on-top {
    z-index: 10;
    position: relative;
  }
  .fullscreen-menu {
    overflow-y: scroll;
    display: flex;
    justify-content: space-around;
    transition: top 1s ease-in-out;
    position: absolute;
    top: -100vh;
    left: 0;
    width: 100%;
    height: 100vh;
    background: rgba(0, 0, 0, 0.40);
    backdrop-filter: blur(38px);
    z-index: 5;
    .fullscreen-menu__list {
      padding-top: 100px;
      width: 100%;
      ul {
        list-style: none;
        padding: 0;
        display: flex;
        flex-direction: column;
        align-items: center;
        gap: 30px;
      }
      li.anim-hover {
        width: fit-content;
        margin: 0;
        position: relative;
        cursor: pointer;
        .anim-hover__title {
          transition: color 1s ease;
          opacity: 1;
          width: 100%;
        }
        .anim-hover__line {
          position: absolute;
          bottom: 0;
          left: 0;
          width: 0;
          height: 20px;
          background: #F4EDDE;
          transition: width 1s ease, background-color 1s ease;
        }
        &:hover {
          .anim-hover__title {
            //color: #ccc;
            //color: #BFC0C0;
          }
          .anim-hover__line {
            width: 100%; // Cela étend la largeur de la ligne à 100% de son conteneur
            background-color: #ffffff; // Mettez la couleur que vous souhaitez
          }
        }
      }
    }
  }
}
</style>


<script setup>
import { gsap } from "gsap";

const menuIsOpen = ref(false);
const router = useRouter();

let isAnimating = false;
let menuClickListener;

function animateTextElements() {
  const textElements = document.querySelectorAll(".fullscreen-menu .anim-hover__title");
  textElements.forEach((el, index) => {
    gsap.to(el, {duration: 1, opacity: 1, delay: index * 0.5});
  });
}

function reverseAnimateTextElements() {
  const textElements = document.querySelectorAll(".fullscreen-menu .anim-hover__title");
  textElements.forEach((el, index) => {
    gsap.to(el, {duration: 1, opacity: 0, delay: index * 0.5});
  });
}

const toggleMenu = () => {
  if (isAnimating) return;

  isAnimating = true;

  const menuText = document.getElementById("menu-text");
  const fullscreenMenu = document.getElementById("fullscreen-menu");


  if (menuIsOpen.value) {
    reverseAnimateTextElements();
    setTimeout(() => {
      fullscreenMenu.style.top = "-100vh";
      menuText.innerText = "menu";
      isAnimating = false;
    }, 2000);
  } else {
    fullscreenMenu.style.top = "0";
    menuText.innerText = "close";
    setTimeout(() => {
      animateTextElements();
      isAnimating = false;
    }, 1000);
  }

  menuIsOpen.value = !menuIsOpen.value;
};


onMounted(() => {
  const menuIcon = document.getElementById("menu-icon");

  menuClickListener = toggleMenu;
  menuIcon.addEventListener("click", menuClickListener);

  router.beforeEach((to, from, next) => {
    menuIsOpen.value = false;

    const fullscreenMenu = document.getElementById("fullscreen-menu");
    const menuText = document.getElementById("menu-text");

    reverseAnimateTextElements();

    fullscreenMenu.classList.add('no-transition');
    fullscreenMenu.style.top = "-100vh";
    menuText.innerText = "menu";
    setTimeout(() => {
      fullscreenMenu.classList.remove('no-transition');
    }, 0);

    next();
  });

});

  onBeforeUnmount(() => {
    const menuIcon = document.getElementById("menu-icon");
    menuIcon.removeEventListener("click", menuClickListener);

  });
</script>

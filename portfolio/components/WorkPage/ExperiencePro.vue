<script setup lang="js">
onMounted(() => {
  const container = document.querySelector('.container');
  let projects = Array.from(document.querySelectorAll('.project'));

  let cumulativeTop = 0;

  const updateProjects = () => {
    cumulativeTop = 0;
    projects.forEach((project, index) => {
      if (index !== 0) {
        cumulativeTop += 40;
      }
      project.style.top = `${cumulativeTop}px`;
    });
  };

  const observer = new IntersectionObserver(entries => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        entry.target.classList.add('stuck');
      } else {
        entry.target.classList.remove('stuck');
      }
    });
  }, {
    root: container,
    threshold: 0.1
  });

  projects.forEach(project => observer.observe(project));

  container.addEventListener('scroll', () => {
    projects = Array.from(document.querySelectorAll('.project'));
    updateProjects();

    if (window.innerWidth >= 1024) {
      for (let i = 0; i < projects.length; i++) {
        const project = projects[i];
        const nextProject = projects[i + 1];
        const h1Element = project.querySelector('.project-title');

        if (project.classList.contains('stuck') && nextProject) {
          const projectRect = project.getBoundingClientRect();
          const nextProjectRect = nextProject.getBoundingClientRect();

          const overlap = (projectRect.bottom - 80) - nextProjectRect.top;

          if (overlap > 0) {
            const scale = Math.max(50, 128 - (100 * (overlap / nextProjectRect.height)));
            h1Element.style.fontSize = `${scale}px`;
          } else {
            h1Element.style.fontSize = '128px';
          }
        } else {
          h1Element.style.fontSize = '128px';
        }
      }
    }
  });
});
</script>

<template>
  <section class="wrapper wrapper-container">
    <p class="">
      Featured works
    </p>
    <article class="container">
      <div class="project">
        <div class="container-title">
          <h1 class="h2 project-title">
            TitoMojito
          </h1>
          <a href="https://tito-mojito.vercel.app" target="_blank" class="project-git">
            See Project
          </a>
        </div>
        <div class="project-description">
          <p>
            Showcase site developed in Nuxt3/GSAP and Wordpress (site in pre-production)
          </p>
        </div>
        <div class="project-collaborateurs">
          <div>
            <h2>
              W /
            </h2>
          </div>
          <div>
            <h2>
              Stacks /
            </h2>
            <div>
              <ul>
                <li>
                  Nuxt3/GSAP
                </li>
                <li>
                  WordPress Headless
                </li>
              </ul>
            </div>
          </div>
          <div>
            <h2>
              Role / Developer & UI/UX Design
            </h2>
          </div>
        </div>
      </div>
      <div class="project">
        <div class="container-title">
          <h1 class="h2 project-title">
            OnePiece MiniGames
          </h1>
          <a href="https://github.com/tifiloutube/React-OnePiece" target="_blank" class="project-git">
            See Project
          </a>
        </div>
        <div class="project-description">
          <p>
            Site with onePiece mini-games as well as a wiki for a school project
          </p>
        </div>
        <div class="project-collaborateurs">
          <div>
            <h2>
              W / YNOV
            </h2>
          </div>
          <div>
            <h2>
              Stacks /
            </h2>
            <div>
              <ul>
                <li>
                  React
                </li>
              </ul>
            </div>
          </div>
          <div>
            <h2>
              Role / Developer
            </h2>
          </div>
        </div>
      </div>
      <div class="project">
        <div class="container-title">
          <h1 class="h2 project-title">
            Happy Birthday Mailer
          </h1>
          <NuxtLink class="project-git private">
          See Project
          </NuxtLink>
        </div>
        <div class="project-description">
          <p>
            MicroService allowing the sending of automated emails every day to customers registered on an e-commerce site whose birthday it is with a promotional code.
          </p>
        </div>
        <div class="project-collaborateurs">
          <div>
            <h2>
              W /
              <NuxtLink to="https://thisispam.com/" class="" target="_blank">
                PAM
              </NuxtLink>
            </h2>
          </div>
          <div>
            <h2>
              Stacks /
            </h2>
            <div>
              <ul>
                <li>
                  NodeJS
                </li>
                <li>
                  API Shopify
                </li>
              </ul>
            </div>
          </div>
          <div>
            <h2>
              Role / Developer
            </h2>
          </div>
        </div>
      </div>
      <div class="project">
        <div class="container-title">
          <h1 class="h2 project-title">
            Waiting List
          </h1>
          <NuxtLink class="project-git private">
            See Project
          </NuxtLink>
        </div>
        <div class="project-description">
          <p>
            Microservice allowing users to add themselves to a waiting list if the product is no longer in stock on the site.
          </p>
        </div>
        <div class="project-collaborateurs">
          <div>
            <h2>
              W /
              <NuxtLink to="https://thisispam.com/" class="" target="_blank">
                PAM
              </NuxtLink>
            </h2>
          </div>
          <div>
            <h2>
              Stacks /
            </h2>
            <ul>
              <li>
                JavaScript
              </li>
              <li>
                NodeJS
              </li>
              <li>
                API Shopify
              </li>
            </ul>
          </div>
          <div>
            <h2>
              Role / Developer
            </h2>
          </div>
        </div>
      </div>
      <div class="project">
        <div class="container-title">
          <h1 class="h2 project-title">
            Mailjet Add List
          </h1>
          <NuxtLink class="project-git private">
            See Project
          </NuxtLink>
        </div>
        <div class="project-description">
          <p>
            Microservice allowing users to add themselves to a newsletter managed via mailjet from the site.
          </p>
        </div>
        <div class="project-collaborateurs">
          <div>
            <h2>
              W /
              <NuxtLink to="https://thisispam.com/" class="" target="_blank">
                PAM
              </NuxtLink>
            </h2>
          </div>
          <div>
            <h2>
              Stacks /
            </h2>
            <ul>
              <li>
                JavaScript
              </li>
              <li>
                NodeJS
              </li>
              <li>
                API MailJet
              </li>
            </ul>
          </div>
          <div>
            <h2>
              Role / Developer
            </h2>
          </div>
        </div>
      </div>
      <div class="project">
        <div class="container-title">
          <h1 class="h2 project-title">
            Arty Agency
          </h1>
          <NuxtLink to="https://github.com/MrBartou/Arti-Agency" class="project-git" target="_blank">
            See Project
          </NuxtLink>
        </div>
        <div class="project-description">
          <p>
            School project where we developed a showcase site for a creative web agency with a dashboard that allows you to manage projects and tasks on the project.
          </p>
        </div>
        <div class="project-collaborateurs">
          <div>
            <h2>
              W /
              <NuxtLink to="https://www.ynov.com/campus/toulouse/" class="" target="_blank">
                YNOV
              </NuxtLink>
            </h2>
          </div>
          <div>
            <h2>
              Stacks /
            </h2>
            <ul>
              <li>
                Angular
              </li>
              <li>
                GSAP
              </li>
            </ul>
          </div>
          <div>
            <h2>
              Role / Developer
            </h2>
          </div>
        </div>
      </div>
      <div class="project">
        <div class="container-title">
          <h1 class="h2 project-title">
            API Netwish
          </h1>
          <NuxtLink to="https://github.com/MrBartou/api_netwish" class="project-git" target="_blank">
            See Project
          </NuxtLink>
        </div>
        <div class="project-description">
          <p>
            School project where we developed an API allowing you to retrieve all available films/series with the synopsis and rating
          </p>
        </div>
        <div class="project-collaborateurs">
          <div>
            <h2>
              W /
              <NuxtLink to="https://www.ynov.com/campus/toulouse/" class="" target="_blank">
                YNOV
              </NuxtLink>
            </h2>
          </div>
          <div>
            <h2>
              Stacks /
            </h2>
            <ul>
              <li>
                NodeJS
              </li>
            </ul>
          </div>
          <div>
            <h2>
              Role / Developer
            </h2>
          </div>
        </div>
      </div>
      <div class="project">
        <div class="container-title">
          <h1 class="h2 project-title">
            Foodie Roulette
          </h1>
          <NuxtLink to="https://github.com/tifiloutube/foodie-roulette" class="project-git" target="_blank">
            See Project
          </NuxtLink>
        </div>
        <div class="project-description">
          <p>
            School project where we developed an Android application which allows users, depending on their location, to know where to eat by retrieving all the restaurants in the surrounding area over a distance selected by the user and which suggests a place to eat according to all the restaurants in the area.
          </p>
        </div>
        <div class="project-collaborateurs">
          <div>
            <h2>
              W /
              <NuxtLink to="https://www.ynov.com/campus/toulouse/" class="" target="_blank">
                YNOV
              </NuxtLink>
            </h2>
          </div>
          <div>
            <h2>
              Stacks /
            </h2>
            <ul>
              <li>
                Java
              </li>
            </ul>
          </div>
          <div>
            <h2>
              Role / Developer
            </h2>
          </div>
        </div>
      </div>
      <div class="project noMoreProject">
        <h2 class="h2 noMoreProject-title">No more projects available at the moment, do not hesitate to come back later.</h2>
      </div>
    </article>
  </section>
</template>

<style scoped>
.container {
  height: calc(100vh - 175px);
  overflow: auto;
  display: grid;
  gap: 50px;
  .project {
    border-top: 1px #F4EDDE solid;
    background-color: #212121;
    .container-title {
      display: flex;
      justify-content: space-between;
      .project-git {
        margin-top: 10px;
      }
      .private {
        text-decoration-line: line-through;
      }
    }
    .project-title {

    }

    .project-description {
      max-width: 400px;
    }

    .project-collaborateurs {
      display: flex;
      justify-content: space-between;
    }
  }
  .noMoreProject {
    z-index: 1;
    height: calc(100vh - 160px);
    background-color: #212121;
    text-align: left;
    .noMoreProject-title {
      height: 100%;
      display: flex;
      align-items: center;
      justify-content: center;
      margin: auto;
    }
  }
}

ul {
  list-style: none;
  padding: 0;
  margin: 0;
}

.stuck {
  position: sticky;
  top:0;
}

@media screen and (max-width: 600px) {
  .project {
    height: 35vh;
  }
}
</style>
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

    for (let i = 0; i < projects.length; i++) {
      const project = projects[i];
      const nextProject = projects[i + 1];
      const h1Element = project.querySelector('.project-title');

      if (project.classList.contains('stuck') && nextProject) {
        const projectRect = project.getBoundingClientRect();
        const nextProjectRect = nextProject.getBoundingClientRect();

        const overlap = (projectRect.bottom - 80) - nextProjectRect.top;

        if (overlap > 0) {
          const scale = Math.max(50, 196 - (146 * (overlap / nextProjectRect.height)));
          h1Element.style.fontSize = `${scale}px`;
        } else {
          h1Element.style.fontSize = '196px';
        }
      } else {
        h1Element.style.fontSize = '196px';
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
        <h1 class="h1 project-title">
          Happy Birthday Mailer
        </h1>
        <div class="project-description">
          <p>
            MicroService allowing the sending of automated emails every day to customers registered on an e-commerce site whose birthday it is with a promotional code.
          </p>
        </div>
        <div class="project-collaborateurs">
          <div>
            <h2>
              W /
              <a href="https://thisispam.com/" class="">
                PAM
              </a>
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
        <h1 class="h1 project-title">
          Waiting List
        </h1>
        <div class="project-description">
          <p>
            Microservice allowing users to add themselves to a waiting list if the product is no longer in stock on the site.
          </p>
        </div>
        <div class="project-collaborateurs">
          <div>
            <h2>
              W /
              <a href="https://thisispam.com/" class="">
                PAM
              </a>
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
        <h1 class="h1 project-title">
          Mailjet Add List
        </h1>
        <div class="project-description">
          <p>
            Microservice allowing users to add themselves to a newsletter managed via mailjet from the site.
          </p>
        </div>
        <div class="project-collaborateurs">
          <div>
            <h2>
              W /
              <a href="https://thisispam.com/" class="">
                PAM
              </a>
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
        <h1 class="h1 project-title">
          Arty Agency
        </h1>
        <div class="project-description">
          <p>
            School project where we developed a showcase site for a creative web agency with a dashboard that allows you to manage projects and tasks on the project.
          </p>
        </div>
        <div class="project-collaborateurs">
          <div>
            <h2>
              W /
              <a href="https://www.ynov.com/campus/toulouse/" class="">
                YNOV
              </a>
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
        <h1 class="h1 project-title">
          API Netwish
        </h1>
        <div class="project-description">
          <p>
            School project where we developed an API allowing you to retrieve all available films/series with the synopsis and rating
          </p>
        </div>
        <div class="project-collaborateurs">
          <div>
            <h2>
              W /
              <a href="https://www.ynov.com/campus/toulouse/" class="">
                YNOV
              </a>
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
        <h1 class="h1 project-title">
          Foodie Roulette
        </h1>
        <div class="project-description">
          <p>
            School project where we developed an Android application which allows users, depending on their location, to know where to eat by retrieving all the restaurants in the surrounding area over a distance selected by the user and which suggests a place to eat according to all the restaurants in the area.
          </p>
        </div>
        <div class="project-collaborateurs">
          <div>
            <h2>
              W /
              <a href="https://www.ynov.com/campus/toulouse/" class="">
                YNOV
              </a>
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
        <h1 class="h1 noMoreProject-title">No more projects available at the moment, do not hesitate to come back later.</h1>
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
</style>
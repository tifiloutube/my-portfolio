<script setup lang="ts">

</script>

<template>
  <section class="container">
    <div class="wrapper">
      <div class="topBlock">
        <p class="topBlock-text">About me</p>
        <span class="line"></span>
      </div>
      <h2 class="h2 title">Vilarinho Philippe</h2>
      <div class="description">
        <section>
          <p>Frontend Developer</p>
          <p class="text">Combining aesthetics and usefulness, I create solid user interfaces in an artistic way. I love to spend time improving the aesthetics of digital products without forgetting about usability. <br>
            I am is a user interface designer working with agencies and startups worldwide to tackle complex projects. Having collaborated with clients, Olacodes knows what it’s like to create, design and develop complex user interfaces.</p>
        </section>
        <article>
          <ul class="listInterest">
            <li>
              Interest
            </li>
            <li>
              Frontend Developer
            </li>
            <li>
              Creative Development
            </li>
            <li>
              Art Direction
            </li>
            <li>
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
    .line {
      display: inline-block;
      height: 1px;
      background-color: #212121;
      width: 100%;
    }
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
</style>
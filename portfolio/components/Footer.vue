<script setup lang="ts">

</script>

<template>
  <footer class="wrapper footer">
    <div>
      <NuxtLink to="mailto:philippe.vilarinhocerqueira@gmail.com">
        philippe.vilarinhocerqueira@gmail.com
      </NuxtLink>
    </div>
    <div class="linkSite">
      <NuxtLink to="https://github.com/tifiloutube" target="blank" class="link">
        Github
        <svg xmlns="http://www.w3.org/2000/svg" width="16" height="17" viewBox="0 0 16 17" fill="none">
          <path d="M11.456 3.16165L1.35906 3.16165L1.35908 0.500023L16 0.5L16 15.1409L13.3384 15.1409L13.3384 5.044L1.88235 16.5L0 14.6176L11.456 3.16165Z" fill="#212121"/>
        </svg>
      </NuxtLink>
      <a href="https://www.linkedin.com/in/philippe-vilarinho-893a07161/" target="blank" class="link">
        LinkedIn
        <svg xmlns="http://www.w3.org/2000/svg" width="16" height="17" viewBox="0 0 16 17" fill="none">
          <path d="M11.456 3.16165L1.35906 3.16165L1.35908 0.500023L16 0.5L16 15.1409L13.3384 15.1409L13.3384 5.044L1.88235 16.5L0 14.6176L11.456 3.16165Z" fill="#212121"/>
        </svg>
      </a>
    </div>
  </footer>
</template>

<style scoped>
  .footer {
    display: flex;
    justify-content: space-between;
    .linkSite {
      display: flex;
      gap: 55px;
      .link {
        display: flex;
        gap: 10px;
      }
    }
  }
</style>
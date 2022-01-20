<template>
  <v-container>
    <nuxt-link
        to="/home">
        <EnterHome />
    </nuxt-link>
  </v-container>
</template>

<style scoped>
  .home-leave-active {
    animation-timing-function:ease-out;
    animation: home-in 3.0s;
    animation-delay: 1.0s;
    transform-origin: 50% 30%;
  }
  .home-enter-active {
    animation-timing-function:ease-out;
    animation: home-out 3.0s;
  }
  @keyframes home-in {
    0% {
      transform: scale(1);
      opacity: 100;
    }
    100% {
      transform: scale(1.8);
      opacity: 10;
    }
  }
  @keyframes home-out {
    0% {
      opacity: 0;
    }
    100% {
      opacity: 100;
    }
  }
</style>
<script>
export default {
  transition: {
    name: "home",
  }
}
</script>

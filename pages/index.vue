<template>
  <v-app class="parent">
    <nuxt-link to="/home" class="child">
      <div class="enter_background"/>
    </nuxt-link>
  </v-app>
</template>

<style scoped>
  .parent {
    position: relative;
    height: 100vh;
    width: 100vw;
  }
  .enter_background {
      background-image: url("/enter_home.webp");
      background-position: center center;
      background-repeat: no-repeat;
      background-size: cover;
      height: 100vh;
      width: 100vw;
  }
  .child {
    position: absolute;
    height: 100vh;
    width: 100vw;
  }
  .tv-leave-active {
    animation-timing-function:ease-out;
    animation: home-in 3.0s;
    animation-delay: 1.0s;
    transform-origin: center 40%;
  }
  .tv-enter-active {
    animation-timing-function:ease-out;
    animation: home-out 3.0s;
  }
  @keyframes home-in {
    0% {
      transform: scale(1);
      opacity: 1;
    }
    100% {
      transform: scale(2.4);
      opacity: 0.5;
    }
  }
  @keyframes home-out {
    0% {
      opacity: 0;
    }
    100% {
      opacity: 1;
    }
  }
</style>
<script>
export default {
  transition: {
    name: "tv",
    mode: ""
  },
  head () {
      return {
          link: [
              {
                rel: 'preload',
                href: '/girl.webp',
                as: 'image'
              },
              {
                rel: 'preload',
                href: '/signboard.webp',
                as: 'image'
              },
              {
                rel: 'preload',
                href: '/station.webp',
                as: 'image'
              },
              {
                rel: 'preload',
                href: '/vending_machine.webp',
                as: 'image'
              },
              {
                rel: 'preload',
                href: '/walk_sample.gif',
                as: 'image'
              }
          ]
      }
  }
}
</script>

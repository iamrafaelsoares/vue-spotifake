<template>
  <div id="app">
    <nav-bar />
    <router-view />
    <player />
  </div>
</template>

<script>
import NavBar from "./components/NavBar.vue";
import Player from "./components/Player.vue";
export default {
  components: {
    NavBar,
    Player,
  },
  data: () => ({}),
};
</script>

<style lang="sass">
*
  margin: 0
  padding: 0
  box-sizing: border-box

html, body
  height: 100%

#app
  height: 100%
  background-color: #000
  font-family: "Segoe UI", "Arial", sans-serif
</style>

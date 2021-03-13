<template>
  <div id="player">
    <a href="">
      <span class="icon">
        <font-awesome-icon :icon="['far', 'heart']" />
      </span>
    </a>
    <router-link to="/player" class="music">
      <strong>{{ music }}</strong>
      <span>{{ artist }}</span>
    </router-link>
    <a v-if="status === 'play'" @click="pause">
      <span class="icon">
        <font-awesome-icon icon="pause" />
      </span>
    </a>
    <a v-if="status === 'pause'" @click="play">
      <span class="icon">
        <font-awesome-icon icon="play" />
      </span>
    </a>

    <div class="progress-bar">
      <div class="range-bar" ref="rangeBar" style="width: 0%"></div>
    </div>
  </div>
</template>

<script>
export default {
  name: "NavBar",
  props: {},
  data: () => ({
    status: "pause",
    music: "One",
    artist: "Metallica",
  }),
  methods: {
    play() {
      this.status = "play";
      const rangeBar = this.$refs.rangeBar;
      let progress = parseInt(rangeBar.style.width.replace("%"));
      setInterval(() => {
        progress = progress >= 100 ? 0 : progress + 1;
        rangeBar.style.width = `${progress}%`;
      }, 1000);
    },
    pause() {
      this.status = "pause";
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="sass">
#player
  position: fixed
  bottom: 48px
  width: 100%
  height: 48px
  display: flex
  justify-content: space-between
  background-color: #282828
  border-top: 1px solid #181818

  a
    text-align: center
    display: flex
    justify-content: center
    align-items: center
    height: 48px
    color: #c9c9c9
    text-decoration: none
    &.music
      width: 70%
      span
        margin-left: 10px

    .icon
      height: 24px
      width: 64px
      font-size: 24px

    .strong
      height: 48px
      line-height: 48px

  .progress-bar
    position: absolute
    top: 0
    background-color: rgba(255, 255, 255, 0.2)
    width: 100%
    height: 1px
    .range-bar
      background-color: #fff
      height: 2px
</style>

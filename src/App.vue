<template>
  <div id="app">
    <CircleFill :percent="percent" />
  </div>
</template>

<script>
import CircleFill from './components/CircleFill';

export default {
  name: 'app',
  components: {
    CircleFill
  },
  data () {
    return {
      percent: 0,
      delay: 1000,
      duration: 2000,
      start: null,
    }
  },
  mounted() {
    // animate the circle after `this.delay` ms
    setTimeout(() => requestAnimationFrame(this.animate), this.delay);
  },
  methods: {
    animate(tick) {
      // set the initial tick that starts the animation
      if (!this.start) this.start = tick;

      // get the current ms since the start tick
      const current = tick - this.start;

      // if we are past the duration, set it to 100, or calculate percent
      this.percent = current > this.duration
        ? 100
        : 100 * (current / this.duration);

      // stop monitoring animation frames when we reach 100, we're done!
      if (this.percent < 100)
        requestAnimationFrame(this.animate);
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

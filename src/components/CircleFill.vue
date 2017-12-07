<template>
  <svg class="circleFill">
    <circle
      cx="25"
      cy="25"
      r="19"
      stroke="#ed8b00"
      stroke-width="6"
      fill="none"
      :stroke-dasharray="dasharray"
      :stroke-dashoffset="dasharray - ((percent / 100) * dasharray)"
    ></circle>
  </svg>
</template>

<script>
export default {
  name: 'CircleFill',
  data () {
    return {
      dasharray: 119.38052083641213,
    }
  },
  props: {
    percent: Number,
  }
}
</script>

<style scoped>
  .circleFill {
    transition: all 3s;
  }

  circle {
    stroke: red !important;
  }
</style>

<template lang="pug">
  .igs-breakpoint-number(:class='{"igs-breakpoint-numbers-disable": disable}')
    .igs-breakpoint-number-1(:class='{"igs-breakpoint-number-disable": this.currentNumber !== 1}')
      |{{number1}}
    .igs-breakpoint-number-2(:class='{"igs-breakpoint-number-disable": this.currentNumber !== 2}')
      |{{number2}}
</template>

<script>
export default {
  props: {
    currentBreakpoint: {
      type: Object,
      required: true
    },
    enabledTransition: {
      type: Boolean,
      default: true
    }
  },
  data () {
    return {
      number1: '',
      number2: '',
      currentNumber: 1,
      disable: false,
      isInTransition: false
    }
  },
  mounted () {
    if (this.enabledTransition) {
      this.$root.$on('breakpoint-change', this.transition)
    }
    this.transition(this.currentBreakpoint)
  },
  methods: {
    transition (breakpoint) {
      if (breakpoint.number) {
        this.disable = false
        if (this.currentNumber === 1 && breakpoint.number !== this.number1) {
          this.currentNumber = 2
          this.number2 = breakpoint.number
        } else if (breakpoint.number !== this.number2 && breakpoint.number !== this.number2) {
          this.currentNumber = 1
          this.number1 = breakpoint.number
        }
      } else {
        this.disable = true
      }
    }
  }
}
</script>

<style>

.igs-breakpoint-number {
  opacity:1;
  color: #87101e;
  display:block;
  transition: all .50s;
  font-family: 'Merriweather', serif;
  font-size: 2em;
  position: absolute;
  font-weight: 400;
  margin:26.125em 0 0 48em;
}
.igs-breakpoint-27 .igs-breakpoint-number {
  color: #fffcdf;
}
.igs-breakpoint-number-1,
.igs-breakpoint-number-2 {
  opacity: 1;
  transition: all .50s;
  position: absolute;
}
.igs-breakpoint-number-disable {
  opacity:0;
  margin:0 0 0 2em;
}
.igs-breakpoint-numbers-disable {
  opacity:0;
}
</style>

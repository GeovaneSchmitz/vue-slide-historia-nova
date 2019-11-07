<template lang='pug'>
  .igs-index
    toolbar(:currentBreakpoint="currentBreakpoint")
    presentation(:currentBreakpoint="currentBreakpoint")
</template>

<script>
import toolbar from '@/components/toolbar.vue'
import presentation from '@/components/presentation.vue'
import breakpoints from '@/breakpoints'

export default {
  components: {
    toolbar,
    presentation
  },
  data () {
    return {
      breakpoints,
      breakpointIndex: 0,
      currentBreakpoint: breakpoints[0]
    }
  },
  created () {
    this.printBreakpoints = breakpoints.filter((breakpoint) => {
      return !breakpoint.noPrint
    })
  },
  mounted () {
    this.$root.$on('request-to-previous', this.toPrevious)
    this.$root.$on('request-to-next', this.toNext)
    window.addEventListener('keyup', this.keyboardEvent)
  },
  methods: {
    keyboardEvent (event) {
      const keysNextBreakpoint = ['ArrowRight', ' ', 'Enter']
      const keysPreviousBreakpoint = ['ArrowLeft']
      if (keysNextBreakpoint.includes(event.key)) {
        this.toNext()
      } else if (keysPreviousBreakpoint.includes(event.key)) {
        this.toPrevious()
      }
    },
    toNext () {
      if (!(this.breakpointIndex + 1 === this.breakpoints.length)) {
        this.breakpointIndex++
        this.currentBreakpoint = this.breakpoints[this.breakpointIndex]
        this.$root.$emit('breakpoint-change', this.currentBreakpoint)
        if (this.currentBreakpoint.autoplay) {
          setTimeout(this.toNext, this.currentBreakpoint.timeout)
        }
      }
    },
    toPrevious () {
      if (this.breakpointIndex > 0) {
        this.breakpointIndex--
        this.currentBreakpoint = this.breakpoints[this.breakpointIndex]
        this.$root.$emit('breakpoint-change', this.currentBreakpoint)
        if (this.currentBreakpoint.autoplay) {
          setTimeout(this.toPrevious, this.currentBreakpoint.timeout)
        }
      }
    }
  }
}
</script>

<style>

</style>

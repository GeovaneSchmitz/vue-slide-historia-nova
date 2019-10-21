<template lang="pug">
  .igs-presentation-wrapper
    .igs-presentation(:class="`igs-breakpoint-${currentBreakpoint.index}`", ref='presentation')
      appBackground
      appTitle
      appMembers
      appBreakpointLabel(:currentBreakpoint="currentBreakpoint")
</template>

<script>
import appBackground from '@/components/background.vue'
import appTitle from '@/components/presentation-title.vue'
import appMembers from '@/components/members.vue'
import appBreakpointLabel from '@/components/breakpoint-label.vue'
export default {
  components: {
    appBackground,
    appTitle,
    appBreakpointLabel,
    appMembers
  },
  props: {
    currentBreakpoint: {
      type: Object,
      required: true
    }
  },
  data () {
    return {
    }
  },
  mounted () {
    window.addEventListener('resize', this.resize)
    this.resize()
  },
  methods: {
    resize () {
      if ((window.innerWidth / window.innerHeight) > (16 / 9)) {
        const width = (window.innerHeight / 9 * 16)
        this.$refs.presentation.style.height = window.innerHeight + 'px'
        this.$refs.presentation.style.width = width + 'px'
        this.$refs.presentation.style.fontSize = width / 100 + 'px'
      } else {
        this.$refs.presentation.style.height = (window.innerWidth / 16 * 9) + 'px'
        this.$refs.presentation.style.width = window.innerWidth + 'px'
        this.$refs.presentation.style.fontSize = window.innerWidth / 100 + 'px'
      }
    }
  }
}
</script>

<style>
.igs-presentation-wrapper {
  overflow: hidden;
  background-color: #000;
  width: 100vw;
  height: 100vh;
  position: absolute;
  display: flex;
  justify-items: center;
  align-content: center;
  align-items: center;
  z-index: 0;
}
@media (min-aspect-ratio: 16/9) {
  .igs-presentation-wrapper {
    flex-direction: column;
  }
}

.igs-presentation {
  z-index: 0;
  user-select: none;
  background-color: #fff;
  overflow: hidden;
  position: absolute;
}
</style>

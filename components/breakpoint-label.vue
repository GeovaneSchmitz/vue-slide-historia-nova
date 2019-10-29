<template lang="pug">
  .igs-breakpoint-label(:class='{"igs-breakpoint-label-disable": disable}')
    .igs-breakpoint-label-1(:class='{"igs-breakpoint-label-disable": this.currentLabel !== 1}')
      |{{label1}}
    .igs-breakpoint-label-2(:class='{"igs-breakpoint-label-disable": this.currentLabel !== 2}')
      |{{label2}}
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
      label1: '',
      label2: '',
      currentLabel: 1,
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
      if (breakpoint.showLabel) {
        this.disable = false
        if (this.currentLabel === 1 && breakpoint.label !== this.label1) {
          this.currentLabel = 2
          this.label2 = breakpoint.label
        } else if (breakpoint.label !== this.label2 && breakpoint.label !== this.label2) {
          this.currentLabel = 1
          this.label1 = breakpoint.label
        }
      } else {
        this.disable = true
      }
    }
  }
}
</script>

<style>

.igs-breakpoint-label {
  opacity:1;
  color: #87101e;
  display:block;
  transition: all .50s;
  font-family: 'Merriweather', serif;
  font-size: 3em;
  position: absolute;
  font-weight: 400;
  margin:1em 0 0 3.3333em;
}

.igs-breakpoint-label-1,
.igs-breakpoint-label-2 {
  opacity: 1;
  transition: all .50s;
  position: absolute;
  width: 30em
}
.igs-breakpoint-label-disable {
  opacity:0;
  margin-left: -1em;
}
</style>

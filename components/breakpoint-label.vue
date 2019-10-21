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
    this.$root.$on('breakpoint-change', this.trasition)
  },
  methods: {
    trasition (breakpoint) {
      if (breakpoint.showLabel) {
        this.disable = false
        if (this.currentLabel === 1) {
          this.currentLabel = 2
          this.label2 = breakpoint.label
        } else {
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
  color: #1c43db;
  display:block;
  font-size: 12em;
  transition: all .50s;
  font-family: 'Gilroy', sans-serif;
  font-weight: 800;
  font-size: 5em;
  left: 2em;
  top:1em;
  position: absolute;
}
.igs-breakpoint-label-1,
.igs-breakpoint-label-2 {
  opacity: 1;
  transition: all .50s;
  position: absolute;
  margin-left: 0rem;
}
.igs-breakpoint-label-disable {
  opacity:0;
  margin-left: -1rem;

}
</style>

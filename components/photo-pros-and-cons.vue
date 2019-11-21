<template lang="pug">
.igs-photo-wrapper
  .igs-photo-topics-wrapper
    appTopics.igs-photo-topics(:topics="currentBreakpoint.topicsPhoto", ref='topics')
  .igs-photo
    .igs-photo-img
</template>

<script>
import appTopics from '@/components/topics.vue'
export default {
  components: {
    appTopics
  },
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
  mounted () {
    if (this.enabledTransition) {
      this.$root.$on('breakpoint-change', (breakpoint) => {
        this.$refs.topics.topicsChange()(breakpoint.topicsPhoto)
      })
    }
  }
}
</script>

<style scoped>

.igs-photo-wrapper{
  width: 85em;
  height:42.25em;
  margin:10em 0 0 10em;
  position: absolute;
  font-family: 'Merriweather', serif;
  display: none;
  transition: .25s all;
  opacity: 0;
  overflow:hidden;
  justify-content: space-around;
  flex-direction: row;
  align-items: center;
}
.igs-breakpoint-15 .igs-photo-wrapper,
.igs-breakpoint-70 .igs-photo-wrapper,
.igs-breakpoint-80 .igs-photo-wrapper,
.igs-breakpoint-90 .igs-photo-wrapper{
  display:flex;
}
.igs-breakpoint-70 .igs-photo-wrapper,
.igs-breakpoint-80 .igs-photo-wrapper{
  opacity: 1;
}
.igs-photo {
  display: flex;
  flex-direction: column;
  align-items: center;
  opacity: 0;
  transition: .5s all;
  margin-right:-7em;
}
.igs-photo-label {
  font-size: 1.5em;
  font-weight: 400;
  margin-top:1em;
}
.igs-photo-img{
  width: 42em;
  height: 27.82em;
  background-image: url('../assets/pros-e-contras.png');
  background-size: contain;
  background-repeat: no-repeat;
  margin:1em;
  background-position: center;
  border-radius: 0.7em;
}
.igs-breakpoint-70 .igs-photo,
.igs-breakpoint-80 .igs-photo{
  opacity: 1;
  margin:0;
}
.igs-photo-topics-wrapper{
  width: 50em;
  height:42.25em;
}
.igs-breakpoint-15 .igs-photo-topics{
  opacity: 0;
}
.igs-photo-topics{
  width: 50em;
  align-items: center;
  height:42.25em;
  position: absolute;
}
</style>

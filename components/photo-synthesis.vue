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
  height:48.25em;
  overflow: hidden;
  margin:10em 0 0 10em;
  position: absolute;
  font-family: 'Merriweather', serif;
  display: none;
  transition: .25s all;
  opacity: 0;
  justify-content: space-around;
  flex-direction: row;
  align-items: center;
}
.igs-breakpoint-140 .igs-photo-wrapper,
.igs-breakpoint-150 .igs-photo-wrapper,
.igs-breakpoint-160 .igs-photo-wrapper,
.igs-breakpoint-170 .igs-photo-wrapper{
  display:flex;
}
.igs-breakpoint-150 .igs-photo-wrapper,
.igs-breakpoint-160 .igs-photo-wrapper{
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
  width: 60em;
  height:42.25em;
  background-image: url('../assets/sintese.png');
  background-size: contain;
  background-repeat: no-repeat;
  bottom: 0;
  background-position: bottom;
  border-radius: 0.7em;
}
.igs-breakpoint-150 .igs-photo,
.igs-breakpoint-160 .igs-photo{
  opacity: 1;
  margin:0;
}
.igs-photo-topics-wrapper{
  width: 50em;
  height:42.25em;
  margin-bottom: 6em;
}
.igs-breakpoint-140 .igs-photo-topics{
  opacity: 0;
}
.igs-photo-topics{
  width: 50em;
  align-items: center;
  height:42.25em;
  position: absolute;
}
</style>

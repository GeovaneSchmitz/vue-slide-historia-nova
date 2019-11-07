<template lang="pug">
.igs-photo-wrapper
  .igs-photo-topics-wrapper
    appTopics.igs-photo-topics(:topics="currentBreakpoint.topicsPhoto", ref='topics')
  .igs-photo
    .igs-photo-img1
    .igs-photo-img2
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
  height:46em;
  margin:10em 0 0 10em;
  overflow: hidden;
  position: absolute;
  font-family: 'Merriweather', serif;
  display: none;
  transition: .25s all;
  justify-content: space-around;
  flex-direction: row;
  align-items: center;
}
.igs-breakpoint-4 .igs-photo-wrapper,
.igs-breakpoint-50 .igs-photo-wrapper,
.igs-breakpoint-60 .igs-photo-wrapper,
.igs-breakpoint-6 .igs-photo-wrapper{
  display:flex;
}
.igs-breakpoint-4 .igs-photo-wrapper,
.igs-breakpoint-6 .igs-photo-wrapper{
  opacity: 0;
}
.igs-photo {
  display: flex;
  flex-direction: column;
  align-items: center;
  opacity: 0;
  height: 100%;
  transition: .5s all;
  margin-right:-7em;
}
.igs-photo-label {
  font-size: 1.5em;
  font-weight: 400;
  margin-top:1em;
}
.igs-photo-img1{
  width: 39.11em;
  height: 22em;
  background-image: url('../assets/contexto2.jpg');
  background-size: cover;
  margin:1em;
  background-position: center;
  border-radius: 0.7em;
  box-shadow: 0 .21875em .875em 0 rgba(47, 64, 176, 0.3);
}
.igs-photo-img2{
  width: 39.11em;
  height: 22em;
  background-image: url('../assets/contexto1.png');
  background-size: cover;
  background-position: top center;
  border-radius: 0.7em;
}
.igs-breakpoint-50 .igs-photo,
.igs-breakpoint-60 .igs-photo{
  opacity: 1;
  margin:0;
}
.igs-photo-topics-wrapper{
  width: 50em;
  height:42.25em;
}
.igs-photo-topics{
  width: 50em;
  align-items: center;
  margin-bottom: 4em;
  height:42.25em;
  position: absolute;
}
</style>

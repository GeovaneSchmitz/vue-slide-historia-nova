<template lang="pug">
.igs-photo-wrapper
  .igs-photo
    .igs-photo-img
    .igs-photo-label
      |James Harvey Robinson (1863 - 1936)
  .igs-photo-topics-wrapper
    appTopics.igs-photo-topics(:topics="currentBreakpoint.topicsPhoto", ref='topics')
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
  justify-content: space-around;
  flex-direction: row;
  align-items: center;
}
.igs-breakpoint-13 .igs-photo-wrapper,
.igs-breakpoint-14 .igs-photo-wrapper,
.igs-breakpoint-15 .igs-photo-wrapper,
.igs-breakpoint-16 .igs-photo-wrapper{
  display:flex;
}
.igs-breakpoint-13 .igs-photo-wrapper,
.igs-breakpoint-16 .igs-photo-wrapper{
  opacity: 0;
}
.igs-photo {
  display: flex;
  flex-direction: column;
  align-items: center;
  opacity: 0;
  transition: .5s all;
  margin-left:7em;
}
.igs-photo-label {
  font-size: 1.5em;
  font-weight: 400;
  margin-top:1em;
}
.igs-photo-img{
  width: 22.5em;
  height: 30em;
  background-image: url('../assets/James_Harvey.jpg');
  background-size: cover;
  background-position: center;
  border-radius: 0.7em;
  box-shadow: 0 .21875em .875em 0 rgba(47, 64, 176, 0.3);
}
.igs-breakpoint-14 .igs-photo,
.igs-breakpoint-15 .igs-photo,
.igs-breakpoint-16 .igs-photo{
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
  height:42.25em;
  position: absolute;
}
</style>

<template lang="pug">
.igs-photo-wrapper
  .igs-photos
    .igs-photo
      .igs-photo-img.igs-photo-febvre
      .igs-photo-label
        |Lucien Febvre (1878 - 1956)
    .igs-photo
      .igs-photo-img.igs-photo-marc-bloch
      .igs-photo-label
        |Marc Bloch (1886 - 1944)
    .igs-photo
      .igs-photo-img.igs-photo-braudel
      .igs-photo-label
        |Fernand Braudel (1902 - 1985)
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
  overflow: hidden;
  height:46.25em;
  margin:10em 0 0 10em;
  position: absolute;
  font-family: 'Merriweather', serif;
  display: none;
  transition: .25s all;
  opacity: 0;
  align-items: stretch;
  justify-content: space-around;
  flex-direction: column;
}
.igs-breakpoint-12 .igs-photo-wrapper,
.igs-breakpoint-112 .igs-photo-wrapper,
.igs-breakpoint-13 .igs-photo-wrapper,
.igs-breakpoint-14 .igs-photo-wrapper{
  display:flex;
}
.igs-breakpoint-112 .igs-photo-wrapper,
.igs-breakpoint-13 .igs-photo-wrapper{
  opacity: 1;
}
.igs-photos {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: space-between;
  opacity: 0;
  height:24em;
  transition: .5s all;
  margin-right:-7em;
}
.igs-photo{
  display: flex;
  flex-direction: column;
  justify-content: space-around;
  align-items: center;
}
.igs-photo-label {
  font-size: 1.5em;
  font-weight: 400;
  margin-top:1em;
}
.igs-photo-img{
  width: 13.5em;
  height: 18em;
  background-repeat: no-repeat;
  background-size: cover;
  background-position: center;
  border-radius: 0.7em;
  box-shadow: 0 .21875em .875em 0 rgba(47, 64, 176, 0.3);

  background-position: center;
}
.igs-photo-febvre{
  background-image: url('../assets/Febvre.jpg');
}
.igs-photo-marc-bloch{
  background-image: url('../assets/Marc-Bloch.jpg');
}
.igs-photo-braudel{
  background-image: url('../assets/braudel.jpg');
}
.igs-breakpoint-112 .igs-photos,
.igs-breakpoint-13 .igs-photos{
  opacity: 1;
  margin:0;
}
.igs-photo-topics-wrapper{
  width: 100%;
  height:20em;
}
.igs-breakpoint-12 .igs-photo-topics{
  opacity: 0;
}
.igs-photo-topics{
  width: 100%;
  align-items: center;
  height:20em;
  position: absolute;
}
</style>

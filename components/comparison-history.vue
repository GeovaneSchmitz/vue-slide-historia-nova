<template lang="pug">
.igs-comparison-history
  .igs-comparison-history-old-history
    .igs-comparison-history-title
      |Paradigma tradicional
    appTopics.igs-comparison-old-history-topics(:topics="currentBreakpoint.topicsOldHistory", ref='topicsOldHistory')
  .igs-comparison-history-new-history
    .igs-comparison-history-title
      |Nova História
    appTopics.igs-comparison-new-history-topics(:topics="currentBreakpoint.topicsNewHistory", ref='topicsNewHistory')
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
        this.$refs.topicsOldHistory.topicsChange()(breakpoint.topicsOldHistory)
        this.$refs.topicsNewHistory.topicsChange()(breakpoint.topicsNewHistory)
      })
    }
  }
}
</script>

<style>
.igs-comparison-history {
  width:92em;
  height:48.25em;
  margin:3em;
  position: absolute;
  font-family: 'Merriweather', serif;
  display: none;
  justify-content: space-between;
}
.igs-comparison-history-title{
  font-size: 3em;
  font-weight: 400;
  color: #87101e;
}
.igs-comparison-new-history-topics,
.igs-comparison-old-history-topics{
  width: 50em;
  font-size: 0.8em;
  height: calc(100% - 10em);
  margin-top: 10em;
  text-align: justify;
  align-items: center;
}

.igs-breakpoint-7 .igs-comparison-history,
.igs-breakpoint-8 .igs-comparison-history,
.igs-breakpoint-9 .igs-comparison-history,
.igs-breakpoint-10 .igs-comparison-history,
.igs-breakpoint-11 .igs-comparison-history{
  display: flex;
  opacity: 0;
}
.igs-breakpoint-8 .igs-comparison-history,
.igs-breakpoint-9 .igs-comparison-history,
.igs-breakpoint-10 .igs-comparison-history{
  opacity: 1;
  transition: all .25s;
}
.igs-breakpoint-8 .igs-comparison-history-old-history,
.igs-breakpoint-9 .igs-comparison-history-old-history,
.igs-breakpoint-10 .igs-comparison-history-old-history{
  margin-left:0em;
}
.igs-breakpoint-8 .igs-comparison-history-new-history,
.igs-breakpoint-9 .igs-comparison-history-new-history,
.igs-breakpoint-10 .igs-comparison-history-new-history{
  margin-right:0em;
}
.igs-breakpoint-7 .igs-comparison-history-old-history,
.igs-breakpoint-11 .igs-comparison-history-old-history{
  margin-left:-5em;
}
.igs-breakpoint-7 .igs-comparison-history-new-history,
.igs-breakpoint-11 .igs-comparison-history-new-history{
  margin-right:5em;
}
.igs-comparison-history-old-history,
.igs-comparison-history-new-history {
  width:40em;
  transition: all .25s;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  align-items: center;
  height:100%;
}
</style>

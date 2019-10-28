<template lang="pug">
  .igs-breakpoint-topics(:class='{"igs-breakpoint-topic-disable": disable}')
    .igs-breakpoint-topics-1(v-show='this.currentTopics !== 1')
      .igs-breakpoint-topic(v-for='topic in topics1')
        .igs-breakpoint-topic-bullet
          |●
        .igs-breakpoint-topic-content(v-html='topic')
    .igs-breakpoint-topics-2(v-show='this.currentTopics !== 2')
      .igs-breakpoint-topic(v-for='topic in topics2')
        .igs-breakpoint-topic-bullet
          |●
        .igs-breakpoint-topic-content(v-html='topic')
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
      topics1: [],
      topics2: [],
      currentTopics: 1,
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
      if (breakpoint.topics) {
        this.disable = false
        if (this.currentTopics === 1) {
          this.currentTopics = 2
          this.topics2 = breakpoint.topics
        } else {
          this.currentLabel = 1
          this.topics1 = breakpoint.topics
        }
      } else {
        this.disable = true
      }
    }
  }
}
</script>

<style>

.igs-breakpoint-topics {
  opacity:1;
  color: #000;
  display:block;
  transition: all .50s;
  font-family: 'Merriweather', serif;
  position: absolute;
  margin:10em 0 0 10em;
  width: 85em;
  height: 41.25em;
  display: flex;
  justify-items: center;
  align-items: center;
}
.igs-breakpoint-topic {
  margin-bottom: 0.5em;
  font-family: 'Merriweather', serif;
  display: flex;
  font-size: 2em;
  align-items:baseline;
}
.igs-breakpoint-topic-bullet {
  color: #87101e;
  padding-right: .75em;
  font-size: 1.5em;
}
.igs-breakpoint-topic-content {
  text-align: justify;
  line-height: 1.5;
}
.igs-breakpoint-topics-1,
.igs-breakpoint-topics-2 {
  opacity: 1;
  position: absolute;
  transition: all .50s;
  width: 85em;
}
.igs-breakpoint-topic-disable {
  opacity:0;
  margin-left: -1em;

}
</style>

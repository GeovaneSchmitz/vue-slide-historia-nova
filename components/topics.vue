<template lang="pug">
  .igs-breakpoint-topics(:class='{"igs-breakpoint-topics-disable": disable}')
    .igs-breakpoint-topics-1(:class='{"igs-breakpoint-topic-disable": currentTopics !== 1}')
      .igs-breakpoint-topic(v-for='topic in topics1')
        .igs-breakpoint-topic-bullet
          |●
        .igs-breakpoint-topic-content(v-html='topic')
    .igs-breakpoint-topics-2(:class='{"igs-breakpoint-topic-disable": currentTopics !== 2}')
      .igs-breakpoint-topic(v-for='topic in topics2')
        .igs-breakpoint-topic-bullet
          |●
        .igs-breakpoint-topic-content(v-html='topic')
</template>
<script>
export default {
  props: {
    topics: {
      type: Array,
      default () {
        return []
      }
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
    this.transition(this.topics)
  },
  methods: {
    topicsChange () {
      return function (topics) {
        this.transition(topics)
      }.bind(this)
    },
    transition (topics) {
      if (topics) {
        this.disable = false
        if (this.currentTopics === 1) {
          this.currentTopics = 2
          this.topics2 = topics
        } else {
          this.currentTopics = 1
          this.topics1 = topics
        }
      } else {
        this.currentTopics = 0
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
  height: 41.25em;
  display: flex;
  justify-items: center;
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
  line-height: 1.5;
}
.igs-breakpoint-topics-1,
.igs-breakpoint-topics-2 {
  opacity: 1;
  width: 100%;
  position: absolute;
  transition: all .50s;
  margin-left: 0%;

}
.igs-breakpoint-topic-disable {
  opacity:0;
  margin-left: 10%;
}
.igs-breakpoint-topics-disable {
  opacity:0;
}
</style>

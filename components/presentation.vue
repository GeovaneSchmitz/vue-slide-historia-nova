<template lang="pug">
  .igs-presentation-wrapper
    .igs-presentation.igs-presentation-screen(:class="`igs-breakpoint-${currentBreakpoint.index}`", ref='presentation')
      appBackground
      appTitle
      appMembers
      appComparisonHistory
      appBreakpointLabel(:currentBreakpoint="currentBreakpoint")
      appBreakpointTopics(:currentBreakpoint="currentBreakpoint")
      appQuoteCardMentality
    .igs-presentation.igs-presentation-print(v-for="breakpoint in printBreakpoints", :class="`igs-breakpoint-${breakpoint.index}`")
      appBackground
      appTitle
      appMembers
      appComparisonHistory
      appBreakpointLabel(:currentBreakpoint="breakpoint", :enabledTransition="false")
      appBreakpointTopics(:currentBreakpoint="breakpoint", :enabledTransition="false")
      appQuoteCardMentality
</template>

<script>
import appBackground from '@/components/background.vue'
import appTitle from '@/components/presentation-title.vue'
import appMembers from '@/components/members.vue'
import appBreakpointLabel from '@/components/breakpoint-label.vue'
import appBreakpointTopics from '@/components/breakpoint-topics.vue'
import appComparisonHistory from '@/components/comparison-history.vue'
import appQuoteCardMentality from '@/components/quote-card-mentality.vue'
export default {
  components: {
    appBackground,
    appTitle,
    appBreakpointLabel,
    appBreakpointTopics,
    appMembers,
    appComparisonHistory,
    appQuoteCardMentality
  },
  props: {
    currentBreakpoint: {
      type: Object,
      default () {
        return {}
      }
    },
    print: {
      type: Boolean,
      default: false
    },
    printBreakpoints: {
      type: Array,
      default () {
        return []
      }
    }
  },
  data () {
    return {
    }
  },
  mounted () {
  },
  methods: {
  }
}
</script>

<style>

.igs-presentation {
  z-index: 0;
  user-select: none;
  background-color: #fff;
  overflow: hidden;
  display:none;
}

@media screen {
  .igs-presentation-screen{
    display: block;
  }
  .igs-presentation-wrapper {
    overflow: hidden;
    background-color: #000;
    width: 100vw;
    height: 100vh;
    position: absolute;
    display: flex;
    justify-items: center;
    align-content: center;
    align-items: center;
    z-index: 0;
  }
  .igs-presentation {
    height: 56.25vw;
    width: 100vw;
    font-size: 1vw;
    position: absolute;
  }
}
@media screen and (min-aspect-ratio: 16/9) {
  .igs-presentation-wrapper {
    flex-direction: column;
  }
  .igs-presentation {
    height:100vh;
    width: 177.77777777vh;
    font-size: 1.7777777777vh;
  }
}
@media print {
  .igs-presentation {
    width: 1920px !important;
    height: 1080px !important;
    font-size: 19.2px !important;
  }
  .igs-presentation-print{
    display: block;
  }
}
</style>

<template lang="pug">
  .igs-presentation-wrapper
    .igs-presentation.igs-presentation-screen(:class="`igs-breakpoint-${currentBreakpoint.index}`", ref='presentation')
      appBackground
      appTitle
      appMembers
      appComparisonHistory(:currentBreakpoint="currentBreakpoint")
      appBreakpointLabel(:currentBreakpoint="currentBreakpoint")
      appPhotoProsAndCons(:currentBreakpoint="currentBreakpoint")
      appPhotoHarvey(:currentBreakpoint="currentBreakpoint")
      appPhotoFruin(:currentBreakpoint="currentBreakpoint")
      appPhotoContext(:currentBreakpoint="currentBreakpoint")
      appPhotoNewHistory(:currentBreakpoint="currentBreakpoint")
      appPhotoExplication(:currentBreakpoint="currentBreakpoint")
      appPhotoSynthesis(:currentBreakpoint="currentBreakpoint")
      appPhotoDefinition(:currentBreakpoint="currentBreakpoint")
      appPhotoSource(:currentBreakpoint="currentBreakpoint")
      appBreakpointNumber(:currentBreakpoint="currentBreakpoint")
      appTopics.igs-presentation-topics(ref='topics', :topics="currentBreakpoint.topics")
      appQuoteCardMentality
    .igs-presentation.igs-presentation-print(v-for="breakpoint in printBreakpoints", :class="`igs-breakpoint-${breakpoint.index}`")
      appBackground
      appTitle
      appMembers
      appComparisonHistory(:currentBreakpoint="breakpoint", :enabledTransition="false")
      appBreakpointLabel(:currentBreakpoint="breakpoint", :enabledTransition="false")
      appPhotoHarvey(:currentBreakpoint="breakpoint", :enabledTransition="false")
      appPhotoFruin(:currentBreakpoint="breakpoint", :enabledTransition="false")
      appPhotoContext(:currentBreakpoint="breakpoint", :enabledTransition="false")
      appPhotoProsAndCons(:currentBreakpoint="breakpoint", :enabledTransition="false")
      appPhotoExplication(:currentBreakpoint="breakpoint", :enabledTransition="false")
      appPhotoSynthesis(:currentBreakpoint="breakpoint", :enabledTransition="false")
      appPhotoNewHistory(:currentBreakpoint="breakpoint", :enabledTransition="false")
      appPhotoDefinition(:currentBreakpoint="breakpoint", :enabledTransition="false")
      appPhotoSource(:currentBreakpoint="breakpoint", :enabledTransition="false")
      appBreakpointNumber(:currentBreakpoint="breakpoint", :enabledTransition="false")
      appTopics.igs-presentation-topics(:topics="breakpoint.topics")
      appQuoteCardMentality
</template>

<script>
import appBackground from '@/components/background.vue'
import appTitle from '@/components/presentation-title.vue'
import appMembers from '@/components/members.vue'
import appBreakpointLabel from '@/components/breakpoint-label.vue'
import appPhotoHarvey from '@/components/photo-james-harvey.vue'
import appPhotoContext from '@/components/photo-context.vue'
import appPhotoFruin from '@/components/photo-robert-fruin.vue'
import appPhotoSource from '@/components/photo-source.vue'
import appPhotoSynthesis from '@/components/photo-synthesis.vue'
import appPhotoExplication from '@/components/photo-explication.vue'
import appPhotoNewHistory from '@/components/photo-new-history.vue'
import appPhotoProsAndCons from '@/components/photo-pros-and-cons.vue'
import appPhotoDefinition from '@/components/photo-definition.vue'
import appBreakpointNumber from '@/components/breakpoint-number.vue'
import appTopics from '@/components/topics.vue'
import appComparisonHistory from '@/components/comparison-history.vue'
import appQuoteCardMentality from '@/components/quote-card-mentality.vue'
export default {
  components: {
    appBackground,
    appTitle,
    appBreakpointLabel,
    appTopics,
    appMembers,
    appPhotoDefinition,
    appPhotoHarvey,
    appPhotoContext,
    appPhotoExplication,
    appPhotoNewHistory,
    appPhotoSynthesis,
    appPhotoSource,
    appPhotoProsAndCons,
    appPhotoFruin,
    appComparisonHistory,
    appQuoteCardMentality,
    appBreakpointNumber
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
    this.$root.$on('breakpoint-change', (breakpoint) => {
      this.$refs.topics.topicsChange()(breakpoint.topics)
    })
  },
  methods: {
  }
}
</script>

<style>
.igs-presentation-topics{
  margin:10em 0 0 10em;
  width: 85em;
  align-items: center;
  position: absolute;
  text-align: justify;
}
.igs-presentation {
  z-index: 0;
  user-select: none;
  background-color: #fffcdf;
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

<template lang="pug">
  .igs-presentation-wrapper
    .igs-presentation(:class="`igs-breakpoint-${currentBreakpoint.index}`", ref='presentation')
      appBackground
      appTitle
      appMembers
      appBreakpointLabel(:currentBreakpoint="currentBreakpoint")
      appQuoteCardMentality
</template>

<script>
import appBackground from '@/components/background.vue'
import appTitle from '@/components/presentation-title.vue'
import appMembers from '@/components/members.vue'
import appBreakpointLabel from '@/components/breakpoint-label.vue'
import appQuoteCardMentality from '@/components/quote-card-mentality.vue'
export default {
  components: {
    appBackground,
    appTitle,
    appBreakpointLabel,
    appMembers,
    appQuoteCardMentality
  },
  props: {
    currentBreakpoint: {
      type: Object,
      required: true
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
  z-index: 0;
  user-select: none;
  background-color: #fff;
  overflow: hidden;
  position: absolute;
  height: 56.25vw;
  width: 100vw;
  font-size: 1vw;
}
@media (min-aspect-ratio: 16/9) {
  .igs-presentation-wrapper {
    flex-direction: column;
  }
  .igs-presentation {
    height:100vh;
    width: 177.77777777vh;
    font-size: 1.7777777777vh;
  }
}

</style>

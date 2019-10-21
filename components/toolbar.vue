<template lang="pug">
.igs-toolbar-wrapper(@touchstart="swipe" @touchend="swipe" @click="mouseClick($event)", @mousemove="mouseMove" :class="{'igs-toolbar-hide-cursor': !toolbarActive}")
  .igs-toolbar(:class='{ "igs-toolbar-active": toolbarActive}', @pointerout="toolbarOut", @pointerover="toolbarOver", ref="toolbar")
    .igs-toolbar-button(@click="toolbarToPrevious()")
      |<
    .igs-counter
      |{{currentBreakpoint.label}}
    .igs-toolbar-button(@click="toolbarToNext()")
      |>
</template>

<script>
export default {
  props: {
    currentBreakpoint: {
      type: Object,
      required: true
    }
  },
  data () {
    return {
      timeoutHideToolbar: 1000,
      toolbarActive: false,
      toolbarFocus: false,
      swipeXpos: 0
    }
  },
  methods: {
    toolbarOver () {
      this.toolbarFocus = true
      this.toolbarActive = true
    },
    toolbarOut () {
      if (this.intervalHideToolbar) {
        clearTimeout(this.intervalHideToolbar)
      }
      this.toolbarFocus = false
      this.intervalHideToolbar = setTimeout(() => {
        if (!this.toolbarFocus) {
          this.toolbarActive = false
        }
      }, this.timeoutHideToolbar)
    },
    swipe (event) {
      if (event.srcElement === this.$el) {
        if (event.type === 'touchstart') {
          this.swipeXpos = event.changedTouches[0].clientX
        } else {
          event.preventDefault()
          const swipeXposEnd = event.changedTouches[0].clientX
          if (swipeXposEnd < this.swipeXpos + 10) {
            this.goToNextBreakpoint()
          } else {
            this.goToPreviousBreakpoint()
          }
        }
      }
    },
    toolbarToNext () {
      this.toolbarOut()
      this.goToNextBreakpoint()
    },
    toolbarToPrevious () {
      this.toolbarOut()
      this.goToPreviousBreakpoint()
    },
    mouseClick (event) {
      if (event.srcElement === this.$el) {
        if (!this.toolbarFocus) {
          this.toolbarActive = false
        }
        this.goToNextBreakpoint()
      }
    },
    mouseMove () {
      if (!this.toolbarActive) {
        this.toolbarActive = true
        setTimeout(() => {
          if (!this.toolbarFocus) {
            this.toolbarActive = false
          }
        }, this.timeoutHideToolbar)
      }
    },
    goToPreviousBreakpoint () {
      this.$root.$emit('request-to-previous')
    },
    goToNextBreakpoint () {
      this.$root.$emit('request-to-next')
    }
  }
}
</script>

<style>
.igs-toolbar-wrapper {
  position: absolute;
  width: 100%;
  height: 100%;
  z-index: 2;
  display: flex;
  align-items: flex-end;
  justify-content: center;
}
.igs-toolbar-button,
.igs-counter {
  font-size: 2rem;
  font-family: "Gilroy", sans-serif;
  color: rgba(255, 255, 255, 0.8);
  padding: 0 1rem 0 1rem;
}
.igs-toolbar-hide-cursor {
   cursor: none;
}
.igs-toolbar {
  user-select: none;
  transition: all .250s;
  box-shadow: 0 .21875rem .875rem 0 rgba(47, 64, 176, 0.3);
  background-color: #222;
  height: 48px;
  display: flex;
  justify-content: center;
  align-items: center;
  border-radius: 5px;
  padding: 1rem;
  margin: 2rem;
  opacity: 0;
}
.igs-toolbar-active{
  opacity: 1;
}
</style>

<template lang="pug">
  .igs-title-wrapper
    .igs-title
      |A Nova História
</template>

<script>
export default {

}
</script>

<style>
.igs-breakpoint-0 .igs-title,
.igs-breakpoint-4 .igs-title {
  opacity:0;
  display:block;
}
.igs-breakpoint-0 .igs-title-wrapper,
.igs-breakpoint-4 .igs-title-wrapper {
  opacity:0;
  display: flex;
  right: -10em;
}
.igs-breakpoint-1 .igs-title,
.igs-breakpoint-2 .igs-title,
.igs-breakpoint-3 .igs-title {
  display: block;
}
.igs-breakpoint-1 .igs-title-wrapper,
.igs-breakpoint-2 .igs-title-wrapper,
.igs-breakpoint-3 .igs-title-wrapper {
  height: 100%;
  display: flex;
}
.igs-title {
  display: none;
  transition: all .50s;
  transition-timing-function: cubic-bezier(0.4, 0.0, 0.2, 1);
  font-family: 'Merriweather', serif;
  color: #87101e;
  font-size: 6em;
  margin-bottom: 2em;
}
.igs-title-wrapper {
  transition: all .50s;
  display: flex;
  height: 100%;
  position: absolute;
  align-items: flex-end;
  right: 5em;
  justify-content: center;
  flex-direction: column;
  display: none;
}
</style>

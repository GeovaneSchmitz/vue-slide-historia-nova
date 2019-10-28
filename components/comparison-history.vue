<template lang="pug">
.igs-comparison-history
  .igs-comparison-history-old-history
    .igs-comparison-history-title
      |Paradigma tradicional
  .igs-comparison-history-new-history
    .igs-comparison-history-title
      |Nova História
</template>

<script>
export default {

}
</script>

<style>
.igs-comparison-history {
  width:31em;
  height:16.75em;
  color: #87101e;
  font-size: 3em;
  margin:1em 0 0 1.666em;
  font-weight: 400;
  position: absolute;
  font-family: 'Merriweather', serif;
  display: none;
  justify-content: space-between;
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
  margin:1em 0 0 1.666em;
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
  margin-left:5em;
}
.igs-breakpoint-7 .igs-comparison-history-new-history,
.igs-breakpoint-11 .igs-comparison-history-new-history{
  margin-right:3em;
}
.igs-comparison-history-old-history,
.igs-comparison-history-new-history {
  width:14em;
  transition: all .25s;
  display: flex;
  justify-content: center;
  height:16.75em;
}
</style>

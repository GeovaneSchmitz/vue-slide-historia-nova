<template lang="pug">
  div.igs-background
    .igs-background-cover
      .igs-background-cover-1
</template>

<script>
export default {

}
</script>

<style>
.igs-background {
    background: #fff;
    position: absolute;
    width: 100em;
    height: 100em;
    z-index: -1;
    overflow: hidden;
}

.igs-background-cover{
    background-color: #87101e;
    width: 40em;
    height: 100em;
    z-index: 1;
    transition: all .50s;
    display: block;
    transform: translateX(-35em);
}
.igs-background-cover-1{
    width: 40em;
    height: 100em;
    background-color: #fff;
    z-index: 1;
    transition: all .50s;
    display: none;
}

.igs-breakpoint-0 .igs-background-cover {
    transform: rotate(-15deg) translateY(-10em) translateX(-43em);
}
.igs-breakpoint-0 .igs-background-cover-1,
.igs-breakpoint-1 .igs-background-cover-1,
.igs-breakpoint-4 .igs-background-cover-1 {
    display: block;
    transform: translateX(-44em);
}
.igs-breakpoint-1 .igs-background-cover,
.igs-breakpoint-2 .igs-background-cover,
.igs-breakpoint-3 .igs-background-cover {
    display: block;
    transform: rotate(-15deg) translateY(-10em) translateX(-4em);
}
.igs-breakpoint-2 .igs-background-cover-1,
.igs-breakpoint-3 .igs-background-cover-1 {
    display: block;
    transform: translateX(-5em);
}
</style>

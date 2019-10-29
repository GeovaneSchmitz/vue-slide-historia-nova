<template lang="pug">
  div.igs-background
    .igs-background-ribbon-edge
    .igs-background-ribbon
      .igs-background-ribbon-white
</template>

<script>
export default {

}
</script>

<style>
.igs-background {
    position: absolute;
    width: 100em;
    height: 56.25em;
    z-index: 0;
    overflow: hidden;
}
.igs-background-ribbon-edge{
    position: absolute;
    width: 5em;
    height: 5em;
    margin:54em 0 0 .5em;
    z-index: 2;
    overflow: hidden;
    background-color:#fff;
    transform: rotate(45deg);
    transition: all .50s;
}
.igs-breakpoint-3 .igs-background-ribbon-edge{
    width: 5em;
    height: 5em;
    margin:57.5em 0 0 34.5em;
    z-index: 2;
    background-color:#fff;
    transform: rotate(30deg);
}

.igs-breakpoint-8 .igs-background-ribbon-edge,
.igs-breakpoint-9 .igs-background-ribbon-edge,
.igs-breakpoint-10 .igs-background-ribbon-edge,
.igs-breakpoint-11 .igs-background-ribbon-edge{
    width: 5em;
    height: 5em;
    margin:57.5em 0 0 52.5em;
    z-index: 2;
    background-color:#fff;
    transform: rotate(30deg);
}
.igs-background-ribbon{
    background-color: #87101e;
    width: 40em;
    height: 100em;
    z-index: 1;
    transition: all .50s;
    display: block;
    transform: translateX(-34.5em);
}
.igs-background-ribbon-white{
    width: 35em;
    height: 100em;
    background-color: #fff;
    z-index: 1;
    transition: all .50s ease-out;
    display: block;
}

.igs-breakpoint-0 .igs-background-ribbon-edge,
.igs-breakpoint-1 .igs-background-ribbon-edge,
.igs-breakpoint-2 .igs-background-ribbon-edge,
.igs-breakpoint-9 .igs-background-ribbon-edge {
    display:none;
}
.igs-breakpoint-0 .igs-background-ribbon {
    transform: rotate(-15deg) translateY(-10em) translateX(-43em);
}
.igs-breakpoint-0 .igs-background-ribbon-white,
.igs-breakpoint-1 .igs-background-ribbon-white,
.igs-breakpoint-4 .igs-background-ribbon-white {
    display: block;
    transform: translateX(-47em);
}
.igs-breakpoint-1 .igs-background-ribbon,
.igs-breakpoint-2 .igs-background-ribbon,
.igs-breakpoint-3 .igs-background-ribbon {
    display: block;
    transform: rotate(-15deg) translateY(-10em) translateX(-4em);
}
.igs-breakpoint-7 .igs-background,
.igs-breakpoint-8 .igs-background {
    z-index: 10;
}
.igs-breakpoint-8 .igs-background-ribbon,
.igs-breakpoint-9 .igs-background-ribbon,
.igs-breakpoint-10 .igs-background-ribbon,
.igs-breakpoint-11 .igs-background-ribbon{
    display: block;
    width: 60em;
    transform: rotate(5deg) translateY(-10em) translateX(-10em);
}

.igs-breakpoint-8 .igs-background-ribbon-white,
.igs-breakpoint-9 .igs-background-ribbon-white,
.igs-breakpoint-10 .igs-background-ribbon-white {
    width: 55em;
}
.igs-breakpoint-2 .igs-background-ribbon-white,
.igs-breakpoint-3 .igs-background-ribbon-white {
    display: block;
    transform: translateX(0em);
}
</style>

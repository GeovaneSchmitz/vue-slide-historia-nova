<template lang="pug">
  .igs-members-wrapper
    .igs-member-1
      |Geovane Schmitz
    .igs-member-2
      |Pamela de Oliveira
    .igs-member-3
      |Valter R. Junior
</template>

<script>
export default {

}
</script>

<style>
.igs-member-1,
.igs-member-2,
.igs-member-3 {
  font-family: 'Gilroy', sans-serif;
  color:#000;
  font-size: 3em;
  margin-top: 0.3em;
  transition: all .5s;

}
.igs-breakpoint-0 .igs-members-wrapper,
.igs-breakpoint-4 .igs-members-wrapper {
  display: flex;
  opacity: 0;
}
.igs-breakpoint-1 .igs-members-wrapper,
.igs-breakpoint-2 .igs-members-wrapper,
.igs-breakpoint-3 .igs-members-wrapper{
  display: flex;
  transition: all .5s;
  opacity: 1;
}
.igs-breakpoint-0 .igs-member-2,
.igs-breakpoint-0 .igs-member-3,
.igs-breakpoint-1 .igs-member-2,
.igs-breakpoint-0 .igs-member-1,
.igs-breakpoint-1 .igs-member-3,
.igs-breakpoint-2 .igs-member-3 {
  margin-top: 0.3em;
  opacity: 0;
}
.igs-breakpoint-1 .igs-member-1,
.igs-breakpoint-2 .igs-member-1,
.igs-breakpoint-2 .igs-member-2,
.igs-breakpoint-3 .igs-member-1,
.igs-breakpoint-3 .igs-member-2,
.igs-breakpoint-3 .igs-member-3 {
  margin-top: 0;
  margin-bottom: 0.3em;
  opacity: 1;
}

.igs-members-wrapper {
  transition: all .5s;
  opacity: 0;
  display: none;
  height: calc(100% - 5em);
  position: absolute;
  align-items: flex-end;
  right: 5em;
  justify-content: flex-end;
  flex-direction: column;
}
</style>

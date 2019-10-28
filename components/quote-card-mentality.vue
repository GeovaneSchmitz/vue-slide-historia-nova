<template lang="pug">
.igs-card-quote-card-mentality-wrapper
  .igs-card-quote-card-mentality
    |“De madrugada o rei Francisco I saiu da cama da sua
    |amante para voltar incógnito a seu castelo. Passou
    |(...) em frente de uma igreja bem no momento em
    |que os sinos chamavam para o ofício. Emocionado,
    |ele parou para assistir à missa e orar devotamente.”
    .igs-card-quote-card-mentality-reference
      |Philippe Áries (1990) recordando uma história contada por Febvre
</template>

<script>
export default {

}
</script>

<style>
.igs-card-quote-card-mentality-reference {
    color: rgba(0,0,0,.8);
    font-size: 0.7em;
    margin-top: 1em;
    text-align: right;
    font-family: 'Merriweather', serif;
}
.igs-card-quote-card-mentality-wrapper {
  display:none;
  position: absolute;
  margin:10em 0 0 10em;
  width: 85em;
  height: 41.25em;
  justify-items: center;
  align-items: center;
}
.igs-card-quote-card-mentality {
    text-indent: 1em;
    transition: all .25s, opacity 0.5s;
    font-family: 'Merriweather', serif;
    font-size: 2.5em;
    width: 29em;
    line-height: 1.5;
    text-align: justify;
    padding: 1.5em;
    color: rgba(0,0,0,1);
    border-radius: 0.2em;
    opacity: 1;
    border-right: solid 2em #87101e;
    border-left: solid 0em rgba(255,255,255,0);
    box-shadow: 0 .21875em .875em 0 rgba(47, 64, 176, 0.2);
}
.igs-breakpoint-6 .igs-card-quote-card-mentality,
.igs-breakpoint-8 .igs-card-quote-card-mentality{
    opacity: 0;
    border-left: solid 2em rgba(255,255,255,0);
    border-right: solid 0em #87101e;

}
.igs-breakpoint-6 .igs-card-quote-card-mentality-wrapper,
.igs-breakpoint-7 .igs-card-quote-card-mentality-wrapper,
.igs-breakpoint-8 .igs-card-quote-card-mentality-wrapper {
  display: flex;
}
</style>

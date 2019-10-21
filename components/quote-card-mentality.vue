<template lang="pug">
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
    font-family: Montserrat, sans-serif;
}
.igs-card-quote-card-mentality {
    text-indent: 1em;
    display:none;
    transition: all .25s;
    font-family: 'Merriweather', serif;
    font-size: 2.5em;
    width: 29em;
    margin: 8em 4em;
    line-height: 1.5;
    text-align: justify;
    padding: 1.5em;
    color: rgba(0,0,0,1);
    border-radius: 0.2em;
    border-right: solid 2em #87101e;
    border-left: solid 0em #fff;
    box-shadow: 0 .21875rem .875rem 0 rgba(47, 64, 176, 0.2);
}
.igs-breakpoint-6 .igs-card-quote-card-mentality,
.igs-breakpoint-8 .igs-card-quote-card-mentality{
    opacity: 0;
    color: rgba(0,0,0,0);
    border-left: solid 2em #fff;
    border-right: solid 0em #87101e;

}
.igs-breakpoint-6 .igs-card-quote-card-mentality,
.igs-breakpoint-7 .igs-card-quote-card-mentality,
.igs-breakpoint-8 .igs-card-quote-card-mentality {
    display:block;
}
</style>

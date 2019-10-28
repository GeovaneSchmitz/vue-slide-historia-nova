<template>
  <div>
    <nuxt />
  </div>
</template>
<style>
  body{
    margin: 0;
    padding: 0;
    font-weight: 300;
  }
  @media print {
    @page {
      size: 1920px 1080px;
      padding: 0;
      bleed: 0;
      margin:0cm;
    }
    body{
      margin: 0;
    }
  }
</style>

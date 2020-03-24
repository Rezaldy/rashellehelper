<template>
  <q-page class="q-pa-md index">
    <div class="row q-col-gutter-md">
      <div class="col-xs-12 col-sm-12 col-md-12 col-lg-6 col-xl-6">
        <SpellingTaal class="widget-block q-pa-md"></SpellingTaal>
      </div>
      <div class="col-xs-12 col-sm-12 col-md-12 col-lg-6 col-xl-6">
        <Rekenen class="widget-block q-pa-md"></Rekenen>
      </div>
    </div>
  </q-page>
</template>

<script>
    import SpellingTaal from "../components/SpellingTaal";
    import Rekenen from "../components/Rekenen";
    export default {
        name: 'PageIndex',
        components: {Rekenen, SpellingTaal},
        data() {
            return {
                text: ''
            }
        },
    }
</script>

<style lang="scss">
  .widget-block {
    background: rgba(0, 0, 0, .3);
  }

  .index {
    background: url("~assets/background.jpg") no-repeat center center fixed;
    -webkit-background-size: cover;
    -moz-background-size: cover;
    -o-background-size: cover;
    background-size: cover;
  }
</style>

<template lang="html">
  <div class="wrapper aligner">
    <img class="aside"
    v-bind:src="api_res_poster">
    <div class="main ">
      <span class="title">{{api_res_name}}</span>
      <br /><br />
      {{api_res_overview}}
    </div>
  </div>
</template>

<script>
export default {
  name: 'seeMovie',
  props: ['api_res_name', 'api_res_overview', 'api_res_poster', 'api_res_ID'],
  data () {
    return {
    }
  }
}

</script>

<style lang="css">

.title {
  font-style: italic;
  font-weight: bolder;
  font-size: 18pt;
}

.wrapper {
    margin-left: 20vw;
    margin-right: 20vw;
    display: -ms-inline-flexbox;
    display: -webkit-inline-flex;
    display: inline-flex;
    -webkit-flex-direction: row;
    -ms-flex-direction: row;
    flex-direction: row;
    -webkit-flex-wrap: nowrap;
    -ms-flex-wrap: nowrap;
    flex-wrap: nowrap;
    -webkit-justify-content: flex-start;
    -ms-flex-pack: start;
    justify-content: flex-start;
    -webkit-align-content: center;
    -ms-flex-line-pack: center;
    align-content: center;
    -webkit-align-items: flex-start;
    -ms-flex-align: start;
    align-items: flex-start;
    }

.aside {
    -webkit-order: 0;
    -ms-flex-order: 0;
    order: 0;
    -webkit-flex: 0 1 auto;
    -ms-flex: 0 1 auto;
    flex: 0 1 auto;
    -webkit-align-self: auto;
    -ms-flex-item-align: auto;
    align-self: auto;
    }

.main {
    width: 30vw;
    text-align: left;
    padding-left: 2vw;
    -webkit-order: 0;
    -ms-flex-order: 0;
    order: 0;
    -webkit-flex: 0 1 auto;
    -ms-flex: 0 1 auto;
    flex: 0 1 auto;
    -webkit-align-self: auto;
    -ms-flex-item-align: auto;
    align-self: auto;
    }

.aligner {
  display: flex;
  align-items: center;
  justify-content: center;
}

.aligner-item {
  max-width: 50%;
}

</style>
